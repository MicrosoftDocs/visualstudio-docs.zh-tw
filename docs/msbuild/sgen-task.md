---
title: SGen 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 SGen 工作，藉由包裝 XML 序列化程式產生器工具 Sgen.exe 來建立類型的 XML 序列化元件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 476255e92326b7e9dae950512a5d27871ede2cc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937845"
---
# <a name="sgen-task"></a>SGen 工作

針對指定組件中的型別建立 XML 序列化組件。 這項工作會包裝 XML 序列化程式產生器工具 (*Sgen.exe*) 。 如需詳細資訊，請參閱 [XML 序列化程式產生器工具 ( # A0) ](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe)。

## <a name="parameters"></a>參數

 下表說明 `SGen` 工作的參數。

| 參數 | Description |
|-----------------------------| - |
| `BuildAssemblyName` | 必要的 `String` 參數。<br /><br /> 產生序列化程式碼的組件。 |
| `BuildAssemblyPath` | 必要的 `String` 參數。<br /><br /> 用來產生序列化程式碼之組件的路徑。 |
| `DelaySign` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，則表示您只想將公開金鑰放置於組件中。 如果是 `false`，即表示您想要完整的簽署組件。<br /><br /> 除非與 `KeyFile` 或 `KeyContainer` 參數搭配使用，否則此參數沒有任何作用。 |
| `KeyContainer` | 選擇性的 `String` 參數。<br /><br /> 指定保留金鑰組的容器。 這樣會藉由將公開金鑰插入組件資訊清單中的方式簽署組件。 然後工作將會使用私密金鑰簽署最終組件。 |
| `KeyFile` | 選擇性的 `String` 參數。<br /><br /> 指定用來簽署組件的金鑰組或公開金鑰。 編譯器會將公開金鑰插入組件資訊清單中，然後使用私密金鑰簽署最終組件。 |
| `Platform` | 選擇性的 `String` 參數。<br /><br /> 取得或設定用來產生輸出組件的編譯器平台。 此參數可以具有 `x86`、`x64` 或 `anycpu` 的值。 預設為 `anycpu`。 |
| `References` | 選擇性的 `String[]` 參數。<br /><br /> 指定要求 XML 序列化的型別所參考的組件。 |
| `SdkToolsPath` | 選擇性的 `String` 參數。<br /><br /> 指定 SDK 工具（例如 *resgen.exe*）的路徑。 |
| `SerializationAssembly` | 選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含所產生的序列化組件。 |
| `SerializationAssemblyName` | 選擇性的 `String` 參數。<br /><br /> 指定所產生序列化組件的名稱。 |
| `ShouldGenerateSerializer` | 必要的 `Boolean` 參數。<br /><br /> 如果為 `true`，SGen 工作應該產生序列化組件。 |
| `Timeout` | 選擇性的 `Int32` 參數。<br /><br /> 指定時間量 (以毫秒為單位)，在此時間量之後會終止工作可執行檔。 預設值是 `Int.MaxValue`，表示沒有逾時期間。 |
| `ToolPath` | 選擇性的 `String` 參數。<br /><br /> 指定工作將載入基礎可執行檔的位置， (*sgen.exe*) 。 如果未指定此參數，工作會使用 SDK 安裝路徑，對應至執行 MSBuild 的 framework 版本。 |
| `Types` | 選擇性的 `String[]` 參數。<br /><br /> 取得或設定產生序列化程式碼特定型別的清單。 SGen 只會針對那些型別產生序列化程式碼。 |
| `UseProxyTypes` | 必要的 `Boolean` 參數。<br /><br /> 如果為 `true`，SGen 工作只會為 XML Web 服務 Proxy 型別產生序列化程式碼。 |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
- [工作](../msbuild/msbuild-tasks.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
