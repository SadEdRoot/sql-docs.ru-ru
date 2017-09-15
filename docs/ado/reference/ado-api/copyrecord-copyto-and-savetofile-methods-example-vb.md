---
title: "CopyRecord CopyTo и пример SaveToFile методы (Visual Basic) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- CopyRecord method [ADO], Visual Basic example
- SaveToFile method [ADO], Visual Basic example
- CopyTo method [ADO], Visual Basic example
ms.assetid: 61a51b74-93cd-439c-877f-f3055499d39f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f7e0bdba854ce12456b80a7f42b29f0b6889e9d2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="copyrecord-copyto-and-savetofile-methods-example-vb"></a>CopyRecord CopyTo и пример SaveToFile методы (Visual Basic)
В этом примере демонстрируется создание копии файла с помощью [поток](../../../ado/reference/ado-api/stream-object-ado.md) или [записи](../../../ado/reference/ado-api/record-object-ado.md) объектов. Одной копии веб-папку для публикации в Интернете. Включить других свойств и методов, показанных [тип потока](../../../ado/reference/ado-api/type-property-ado-stream.md), **откройте**, [LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md), и [откройте запись](../../../ado/reference/ado-api/open-method-ado-record.md).  
  
```  
'BeginCopyRecordVB  
  
'Note:  
' This sample requires that "C:\checkmrk.wmf" and  
' "http://MyServer/mywmf.wmf" exist.  
  
Option Explicit  
  
Private Sub Form_Load()  
    On Error GoTo ErrorHandler  
  
    ' Declare variables  
    Dim strPicturePath, strStreamPath, strStream2Path, _  
        strRecordPath, strStreamURL, strRecordURL As String  
    Dim objStream, objStream2 As Stream  
    Dim objRecord As Record  
    Dim objField As Field  
  
    ' Instantiate objects  
    Set objStream = New Stream  
    Set objStream2 = New Stream  
    Set objRecord = New Record  
  
    ' Initialize path and URL strings  
    strPicturePath = "C:\checkmrk.wmf"  
    strStreamPath = "C:\mywmf.wmf"  
    strStreamURL = "URL=http://MyServer/mywmf.wmf"  
    strStream2Path = "C:\checkmrk2.wmf"  
    strRecordPath = "C:\mywmf.wmf"  
    strRecordURL = "http://MyServer/mywmf2.wmf"  
  
    ' Load the file into the stream  
    objStream.Open  
    objStream.Type = adTypeBinary  
    objStream.LoadFromFile (strPicturePath)  
  
    ' Save the stream to a new path and filename  
    objStream.SaveToFile strStreamPath, adSaveCreateOverWrite  
  
    ' Copy the contents of the first stream to a second stream  
    objStream2.Open  
    objStream2.Type = adTypeBinary  
    objStream.CopyTo objStream2  
  
    ' Save the second stream to a different path  
    objStream2.SaveToFile strStream2Path, adSaveCreateOverWrite  
  
    ' Because strStreamPath is a Web Folder, open a Record on the URL  
    objRecord.Open "", strStreamURL  
  
    ' Display the Fields of the record  
    For Each objField In objRecord.Fields  
        Debug.Print objField.Name & ": " & objField.Value  
    Next  
  
    ' Copy the record to a new URL  
    objRecord.CopyRecord "", strRecordURL, , , adCopyOverWrite  
  
    ' Load each copy of the graphic into Image controls for viewing  
    Image1.Picture = LoadPicture(strPicturePath)  
    Image2.Picture = LoadPicture(strStreamPath)  
    Image3.Picture = LoadPicture(strStream2Path)  
    Image4.Picture = LoadPicture(strRecordPath)  
  
    ' clean up  
    objStream.Close  
    objStream2.Close  
    objRecord.Close  
    Set objStream = Nothing  
    Set objStream2 = Nothing  
    Set objRecord = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not objStream Is Nothing Then  
        If objStream.State = adStateOpen Then objStream.Close  
    End If  
    Set objStream = Nothing  
  
    If Not objStream2 Is Nothing Then  
        If objStream2.State = adStateOpen Then objStream2.Close  
    End If  
    Set objStream2 = Nothing  
  
    If Not objRecord Is Nothing Then  
        If objRecord.State = adStateOpen Then objRecord.Close  
    End If  
    Set objRecord = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndCopyRecordVB  
```  
  
## <a name="see-also"></a>См. также:  
 [Метод CopyRecord (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)   
 [CopyTo-метод (ADO)](../../../ado/reference/ado-api/copyto-method-ado.md)   
 [Loadfromfile-метод (ADO)](../../../ado/reference/ado-api/loadfromfile-method-ado.md)   
 [Метод Open (ADO запись)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Метод Open (поток ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Объект записи (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Метод SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)   
 [Объект потока (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [Свойство Type (поток ADO)](../../../ado/reference/ado-api/type-property-ado-stream.md)