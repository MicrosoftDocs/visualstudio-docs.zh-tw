---
title: 錯誤：SQL 可以&#39;t 找不到 SSDEBUGPS |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25462a99bd3e773f03af3918a9e25d11ed006c1c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084709"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>錯誤：SQL 可以&#39;t 找不到 SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll 是 SQL Server 偵錯主機元件。  
  
 當您嘗試啟動偵錯時會發生這個錯誤，並表示指定的檔案不在 [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] 電腦上。 可能的原因是從未執行遠端偵錯 (Remote Debugging) 安裝程式，或者已刪除這個檔案。  
  
 有兩個方法可以解決這個錯誤：一是重新執行遠端偵錯安裝程式，二是將該檔案複製到 [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] 電腦。  
  
 若要重新執行遠端偵錯安裝程式，請遵循指示[遠端偵錯](../debugger/remote-debugging.md)。  
  
 如果找得到 ssdebugps.dll 的複本，就可以將該複本複製到 [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] 電腦。 如果有這個檔案，會在 \Program Files\ Common Files\Microsoft Shared\SQL Debugging 目錄中。 您可能會發現它在另一個[!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]電腦，或在電腦上具有[!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]安裝。  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>若要將 SSDEBUGPS.dll 複製至 SQL Server 2005 電腦  
  
1. 將該檔案複製到 [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] 電腦上具有相同名稱和路徑的目錄。  
  
2. 開啟 [命令提示字元] 並執行下列命令，即可登錄該檔案：  
  
    ```  
    regsvr32 ssdebugps.dll  
    ```
