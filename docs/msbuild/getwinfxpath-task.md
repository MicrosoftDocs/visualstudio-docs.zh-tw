---
title: GetWinFXPath 工作 | Microsoft Docs
description: 瞭解如何使用 MSBuild GetWinFXPath 工作，它會傳回目前 .NET 執行時間的目錄。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 164f9f91eda1d81db00d25bb4e18a6cbb352e41e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914618"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath 工作

此工作會傳回 <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> 目前 .net 執行時間的目錄。

## <a name="task-parameters"></a>工作參數

| 參數 | Description |
|-------------------| - |
| `WinFXPath` | 選擇性 **字串** 輸出參數。<br /><br /> 指定 .NET 執行時間的實際路徑。 |
| `WinFXNativePath` | 必要的 **String** 參數。<br /><br /> 指定原生 .NET 執行時間的路徑。 |
| `WinFXWowPath` | 必要的 **String** 參數。<br /><br /> 指定在64位系統上， **windows 上** 的32位 windows 模組中 .net 元件的路徑。 |

## <a name="remarks"></a>備註

 如果在 64 位元處理器上執行 <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> 工作，**WinFXPath** 參數會設定為 **WinFXWowPath** 參數中儲存的路徑，否則 **WinFXPath** 參數會設定為 **WinFXNativePath** 參數中儲存的路徑。

## <a name="example"></a>範例

 下列範例示範如何使用 **GetWinFXPath** 工作來偵測 .net 執行時間的原生路徑。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GetWinFXPathTask">
    <GetWinFXPath
      WinFXNativePath="c:\WinFXNative"
      WinFXWowPath="c:\WinFXWowNative" />
  </Target>
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />
</Project>
```

## <a name="see-also"></a>另請參閱

- [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)
- [工作參考](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
