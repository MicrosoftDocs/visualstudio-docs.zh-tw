---
title: 錯誤： SQL 可以&#39;t 找不到 SSDEBUGPS |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f775bd99c019a119d1bcd5193df0efd7ceadd096
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180163"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>錯誤： SQL 可以&#39;t 找不到 SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll 是 SQL Server 偵錯主機元件。  
  
 當您嘗試啟動偵錯時會發生這個錯誤，並表示指定的檔案不在 [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] 電腦上。 可能的原因是從未執行遠端偵錯 (Remote Debugging) 安裝程式，或者已刪除這個檔案。  
  
 若要解決此錯誤的兩種方式： 藉由重新執行遠端偵錯安裝程式，並複製檔案拖曳至[!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]機器。  
  
 若要重新執行遠端偵錯安裝程式，請遵循指示[遠端偵錯](../debugger/remote-debugging.md)。  
  
 如果找得到 ssdebugps.dll 的複本，您可以將它拖曳至複製[!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]機器。 如果有這個檔案，會在 \Program Files\ Common Files\Microsoft Shared\SQL Debugging 目錄中。 您可能會發現它在另一個[!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]電腦，或在電腦上具有[!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]安裝。  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>若要將 SSDEBUGPS.dll 複製至 SQL Server 2005 電腦  
  
1.  將檔案複製到具有相同的名稱和路徑的目錄中上,[!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]機器。  
  
2.  註冊 %installationdirectory**命令提示字元**，並執行下列命令：  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```



