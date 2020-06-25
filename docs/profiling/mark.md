---
title: 標記 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b3049a253dca37090d128748b71f278aa2f7e63
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330789"
---
# <a name="mark"></a>標記
*VSPerfCmd.exe 的 [標記]* **** 選項會將指定的資訊插入分析資料檔案中。 個別的 VSPerfReport 報表或分析工具 UI 的標記報表檢視中，則可以列出標記。 [標記]**** 可用以指定報表的起點和終點並檢視篩選。

 [標記]**** 選項必須是命令列上指定的唯一選項。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>參數
 `MarkID` 使用者定義的整數，在分析工具檢視和報表中列為標記識別碼。 `MarkID` 不必是唯一的。

 `MarkName` (選擇性) 使用者定義的字串，在分析工具檢視和報表中列為標記名稱。 如未指定 `MarkName`，標記清單的 [標記名稱] 欄位會是空的。 以引號括住包含空格或正斜線 ("/") 的字串。

## <a name="example"></a>範例
 本例會插入識別碼為 123、標記名稱為的 "TestMark" 的標記。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
