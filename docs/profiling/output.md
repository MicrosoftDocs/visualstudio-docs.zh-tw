---
title: 輸出 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ab01f67d44e8c6e0cc13eaf9b0046695a0132e65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778501"
---
# <a name="output"></a>輸出
[輸出]**** 選項指定效能工作階段的分析資料檔案名稱。 [輸出]**** 必須搭配 [啟動]**** 選項。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>參數
 `FileName` 資料檔案的名稱。 可接受完整和部分路徑。 如未指定路徑，即會在目前的目錄中建立檔案。

## <a name="required-options"></a>必要選項
 [輸出]**** 選項必須搭配 [啟動]**** 選項。

 **開始：** `Method` 指定輸出檔名稱。

## <a name="example"></a>範例
 在以下範例中，分析資料檔案是建立在目前的目錄中。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
