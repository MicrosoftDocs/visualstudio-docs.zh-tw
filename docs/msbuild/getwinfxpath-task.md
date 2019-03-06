---
title: GetWinFXPath 工作 | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c95e5ad882d7021b597d7ba0ad8c38177f4a5136
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646925"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath 工作
<xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> 工作會傳回目前 [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] 執行階段的目錄。

## <a name="task-parameters"></a>工作參數

| 參數 | 說明 |
|-------------------| - |
| `WinFXPath` | 選擇性的 **String** 輸出參數。<br /><br /> 指定 [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)] 執行階段的實際路徑。 |
| `WinFXNativePath` | 必要的 **String** 參數。<br /><br /> 指定原生 [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] 執行階段的路徑。 |
| `WinFXWowPath` | 必要的 **String** 參數。<br /><br /> 指定 64 位元系統上 32 位元 **Windows on Windows** 模組中的 [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] 組件路徑。 |

## <a name="remarks"></a>備註
 如果在 64 位元處理器上執行 <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> 工作，**WinFXPath** 參數會設定為 **WinFXWowPath** 參數中儲存的路徑，否則 **WinFXPath** 參數會設定為 **WinFXNativePath** 參數中儲存的路徑。

## <a name="example"></a>範例
 下列範例示範如何使用 **GetWinFXPath** 工作來偵測 [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] 執行階段的原生路徑。

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
