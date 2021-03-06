---
title: Сжатые моментальные снимки | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], compressed
- snapshot replication [SQL Server], compressed snapshots
- compressed snapshots [SQL Server replication]
ms.assetid: 979ffa7c-3a88-4e70-8cf2-b8d452fd7a7f
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9d871afee6bee2f8dfcf4155d5ea0dbb910b0d87
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="compressed-snapshots"></a>Сжатые моментальные снимки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Сжатие файлов моментальных снимков уместно при передаче моментальных снимков в медленной сети или когда требуется сохранить моментальный снимок на съемный носитель, а объем несжатого моментального снимка превышает свободное место на носителе. Сжатие файлов моментальных снимков полезно в таких случаях, однако сжатие увеличивает время создания и применения моментального снимка.  
  
 Сжатые файлы моментальных снимков записываются в формате [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB, который позволяет сжимать файлы размером до 2 ГБ (если размер файлов моментальных снимков превышает 2 ГБ, их не удастся сжать). Для сжатия файлов их необходимо записать в альтернативную папку моментальных снимков (файлы, записанные в папку моментальных снимков по умолчанию, невозможно сжать). Дополнительные сведения об альтернативных папках моментальных снимков см. в статье [Альтернативные расположения папки моментальных снимков](../../relational-databases/replication/alternate-snapshot-folder-locations.md).  
  
 Файлы распаковываются там, где запущен агент распространителя или агент слияния. Подписки по запросу, как правило, используются со сжатыми моментальными снимками, поэтому файлы распаковываются на подписчике. Когда подписчик получает сжатый файл, первоначально файл записывается во временное местоположение. После копирования сжатого файла подписчику файлы моментальных снимков в сжатом файле распаковываются по очереди при помощи средства распаковки CAB. На подписчике необходимо наличие пространства, равного размеру сжатого файла плюс размер самого большого распакованного файла.  
  
> [!NOTE]  
>  В некоторых случаях сжатые моментальные снимки повышают производительность передачи файлов моментальных снимков по сети. Однако сжатие моментального снимка требует дополнительной обработки, выполняемой агентом моментальных снимков при создании файлов моментальных снимков и агентом распространителя или агентом слияния при применении файлов моментальных снимков. Это может замедлить создание моментального снимка и в некоторых случаях увеличить время, необходимое для применения моментального снимка. Кроме того, сжатые моментальные снимки не могут быть возобновлены в случае сбоя в сети, поэтому они непригодны для ненадежных сетей. Внимательно рассмотрите перечисленные достоинства и недостатки, если планируете применять сжатые моментальные снимки в сети.  
  
 **Сжатие и доставка файлов моментальных снимков**  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Сжатие файлов моментальных снимков (среда SQL Server Management Studio)](../../relational-databases/replication/publish/compress-snapshot-files-sql-server-management-studio.md)  
  
-   Программирование репликации на [!INCLUDE[tsql](../../includes/tsql-md.md)]: [Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>См. также:  
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Параметры моментального снимка](../../relational-databases/replication/snapshot-options.md)  
  
  
