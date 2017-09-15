---
title: "Безопасность DQS | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 921927f5-1b1e-452a-a79e-c691829fd826
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Безопасность DQS
  Инфраструктура обеспечения безопасности [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) основана на инфраструктуре обеспечения безопасности SQL Server. Администратор базы данных предоставляет пользователю набор разрешений, объединяя пользователя с ролью DQS. Это определяет ресурсы служб DQS, к которым пользователь имеет доступ, а также функциональные операции, которые позволено выполнять пользователю.  
  
## Роли DQS  
 Есть четыре роли DQS. Первая роль — администратор базы данных (DBA), который занимается главным образом установкой продукта, обслуживанием базы данных и управлением пользователями. Эта роль в основном используется в среде SQL Server Management Studio, а не в приложении [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Соответствующая роль сервера — sysadmin.  
  
 Три остальные роли — это информационные работники, диспетчеры данных, которые используют продукт непосредственно для работы в приложении [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . К этим ролям относятся следующие роли.  
  
-    **Администратор DQS** (роль dqs_administrator) могут делать все, что в области продукта. Администратор может изменять и выполнять проект, создавать и изменять базу знаний, прерывать любое действие, останавливать процесс в действии, изменять конфигурацию и параметры служб эталонных данных. Но администратор DQS не может устанавливать сервер или добавлять новых пользователей. Эти действия должен выполнять администратор базы данных.  
  
-    **Редактор базы Знаний DQS** (роль dqs_kb_editor) может выполнять все операции DQS, за исключением администрирования. Редактор базы знаний может изменять и выполнять проект, а также создавать и изменять базы знаний. Он может просматривать данные мониторинга активности, но не может прерывать или останавливать действие или выполнение административных обязанностей.  
  
-    **Оператор базы Знаний DQS** (роль dqs_kb_operator) может изменять и выполнять проект. Он не может выполнять управление знаниями любых типов и не может создавать или изменять базы знаний. Он может просматривать данные мониторинга активности, но не может прерывать действие или выполнение административных обязанностей.  
  
## Управление пользователями  
 Администратор базы данных (DBA) создает пользователей DQS и связывает их с ролями DQS в среде SQL Server Management Studio. Администратор базы данных управляет их разрешениями, добавляя имена входа SQL в качестве пользователей базы данных DQS_MAIN и связывая каждого пользователям с одной из ролей DQS. Каждой роли предоставляются разрешения для набора хранимых процедур в базе данных DQS_MAIN. Эти три роли DQS недоступны для баз данных DQS_PROJECTS и DQS_STAGING_DATA.  
  
## Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Описывает, как создать пользователя и предоставить роли DQS с помощью среды SQL Server Management Studio.|[Управление пользователями DQS в среде SSMS](../Topic/Manage%20DQS%20Users%20in%20SSMS.md)|  
  
  