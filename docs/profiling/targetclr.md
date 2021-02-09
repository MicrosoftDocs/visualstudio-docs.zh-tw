---
title: TargetCLR | Microsoft Docs
description: 瞭解 TargetCLR 選項如何指定在應用程式中載入多個版本的 CLR 時，所要分析的通用語言執行時間版本。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 76454a77a895a44d4c6871ad5061ee4b6079e604
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868176"
---
# <a name="targetclr"></a>TargetCLR
**TargetCLR** 選項指定當應用程式載入多個 CLR 版本時要分析的 Common Language Runtime (CLR) 版本。

 根據預設，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具以應用程式載入的第一個 CLR 版本為目標。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>參數
 `ClrVersion` CLR 的版本號碼。 使用版本格式 **vN.N.NNNNN**。

## <a name="required-options"></a>必要選項
 **TargetCLR** 選項僅能與 [啟動] 或 [附加] 選項一起使用。

 **啟動：** `AppName` 啟動指定的應用程式，並開始分析。

 **附加：** `PID` 開始分析指定的進程。

## <a name="example"></a>範例
 本例使用 TargetCLR 選項確定分析的 CLR 版本是 4.0.11003。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
