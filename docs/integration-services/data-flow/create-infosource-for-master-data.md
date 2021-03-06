---
title: Создание InfoSource для основных данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b52a9a89-8380-4a02-8a83-dcfb46ae860e
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5e7db39cd46a786961675b394b9d2269a0cb3b47
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="create-infosource-for-master-data"></a>Создание InfoSource для основных данных
  Используйте диалоговое окно **Создание InfoSource для основных данных** для создания нового InfoSource для основных данных в системе SAP Netweaver BW.  
  
 Диалоговое окно **Создание InfoSource для основных данных** можно открыть на странице **Диспетчер соединений** **Редактора назначений SAP BW**. Дополнительные сведения о назначении SAP BW см. в статье [SAP BW Destination](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
 **Открытие диалогового окна «Создание InfoSource для основных данных»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий назначение SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните назначение SAP BW.  
  
3.  В **Редакторе назначений SAP BW**щелкните **Диспетчер соединений** , чтобы открыть страницу редактора **Диспетчер соединений** .  
  
4.  На вкладке **Диспетчер соединений** в поле группы **Создание объектов SAP BW** выберите **InfoSource**и щелкните **Создать**.  
  
5.  В диалоговом окне **Создание InfoSource** выберите **Основные данные**и нажмите кнопку **ОК**.  
  
## <a name="options"></a>Параметры  
 **Имя InfoObject**  
 Введите имя InfoObject, на основе которого должен быть создан новый InfoSource.  
  
 **Поиск**  
 Поиск InfoObject. Этот параметр открывает диалоговое окно **Поиск InfoObject** , в котором можно выбрать InfoObject. Дополнительные сведения об этом диалоговом окне см. в разделе [Look Up InfoObject](../../integration-services/data-flow/look-up-infoobject.md).  
  
 После выбора InfoObject компонент указывает в текстовом поле **Имя InfoObject** имя выбранного InfoObject.  
  
 **Создать**  
 Создание нового InfoObject Этот параметр открывает диалоговое окно **Создание InfoObject** , в котором можно создать новый InfoObject. Дополнительные сведения об этом диалоговом окне см. в разделе [Create New InfoObject](../../integration-services/data-flow/create-new-infoobject.md).  
  
 После создания InfoObject компонент указывает в текстовом поле **Имя InfoObject** имя нового InfoObject.  
  
 **Краткое описание**  
 Введите краткое описание нового InfoSource.  
  
 **Полное описание**  
 Введите полное описание нового InfoSource.  
  
 **Исходная система**  
 Выберите исходную систему, которая будет связана с новым InfoSource.  
  
 **Приложение**  
 Введите имя приложения, которое необходимо связать с новым InfoSource.  
  
 **Атрибуты**  
 Указывает, что основные данные состоят из атрибутов.  
  
 **Тексты**  
 Указывает, что основные данные состоят из атрибутов.  
  
 **Сохранить и активировать**  
 Сохраните и активируйте новый InfoSource.  
  
## <a name="see-also"></a>См. также:  
 [Создание InfoSource](../../integration-services/data-flow/create-infosource.md)   
 [Справка F1 по соединителю с SAP BW (Microsoft)](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
