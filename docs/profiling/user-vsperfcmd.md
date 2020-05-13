---
title: User (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7dbb1a155e8e0ffd2690b5850299b8075a63ea3d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779957"
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
**User** 選項指定擁有已分析處理序之帳戶的網域和使用者名稱。 只有在以登入的使用者之外的使用者身分執行處理序時，才需要這個選項。 進程擁有者列在 Windows 工作管理員的"**進程"** 選項卡上的"使用者名"列中。

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

 **開始：**`Method`將探測器初始化到指定的分析方法。

## <a name="example"></a>範例
 下列範例示範如何使用 **User** 選項。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [設定檔ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
