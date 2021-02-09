---
title: User (VSPerfCmd) | Microsoft Docs
description: 瞭解使用者選項如何指定擁有已分析進程之帳戶的網域和使用者名稱。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b0240a4dcf0830dca6667bcbd055d677ef7bc204
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885998"
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
**User** 選項指定擁有已分析處理序之帳戶的網域和使用者名稱。 只有在以登入的使用者之外的使用者身分執行處理序時，才需要這個選項。 進程擁有者會列在 Windows 工作管理員的 [ **進程** ] 索引標籤上的 [使用者名稱] 欄中。

 **User** 選項只能指定於也包含 **Start** 選項的命令列。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>參數
 `Domain` 使用者網域的名稱。

 `UserName` 使用者的名稱。

## <a name="required-options"></a>必要選項
 **User** 選項只能與 **Start** 選項搭配使用。

 **開始：** `Method` 將分析工具初始化為指定的分析方法。

## <a name="example"></a>範例
 下列範例示範如何使用 **User** 選項。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
