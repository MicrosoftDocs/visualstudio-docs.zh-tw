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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab8e15cef722e935dde322072f6834ba00be8bc5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633963"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath 工作

該<xref:Microsoft.Build.Tasks.Windows.GetWinFXPath>任務返回當前 .NET 運行時的目錄。

## <a name="task-parameters"></a>工作參數

| 參數 | 描述 |
|-------------------| - |
| `WinFXPath` | 可選**的字串**輸出參數。<br /><br /> 指定 .NET 運行時的實際路徑。 |
| `WinFXNativePath` | 必要的 **String** 參數。<br /><br /> 指定本機 .NET 運行時的路徑。 |
| `WinFXWowPath` | 必要的 **String** 參數。<br /><br /> 在 64 位系統上的**Windows 上的**32 位 Windows 模組中指定 .NET 程式集的路徑。 |

## <a name="remarks"></a>備註

 如果在 64 位元處理器上執行 <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> 工作，**WinFXPath** 參數會設定為 **WinFXWowPath** 參數中儲存的路徑，否則 **WinFXPath** 參數會設定為 **WinFXNativePath** 參數中儲存的路徑。

## <a name="example"></a>範例

 下面的示例演示如何使用**GetWinFXPath**任務來檢測到 .NET 運行時的本機路徑。

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
- [任務引用](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [任務引用](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
