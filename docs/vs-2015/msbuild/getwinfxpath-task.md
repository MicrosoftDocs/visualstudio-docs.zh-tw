---
title: GetWinFXPath 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da32f0bfce9edf652e19df6b68bc51ed92624d80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699030"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> 工作會傳回目前 [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] 執行階段的目錄。  
  
## <a name="task-parameters"></a>工作參數  
  
|參數|描述|  
|---------------|-----------------|  
|`WinFXPath`|選擇性 **字串** 輸出參數。<br /><br /> 指定 [!INCLUDE[TLA2#tla_winfx](../includes/tla2sharptla-winfx-md.md)] 執行階段的實際路徑。|  
|`WinFXNativePath`|必要的 **String** 參數。<br /><br /> 指定原生 [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)] 執行階段的路徑。|  
|`WinFXWowPath`|必要的 **String** 參數。<br /><br /> 指定 64 位元系統上 32 位元 **Windows on Windows** 模組中的 [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] 組件路徑。|  
  
## <a name="remarks"></a>備註  
 如果在 64 位元處理器上執行 <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> 工作，**WinFXPath** 參數會設定為 **WinFXWowPath** 參數中儲存的路徑，否則 **WinFXPath** 參數會設定為 **WinFXNativePath** 參數中儲存的路徑。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 **GetWinFXPath** 工作來偵測 [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)] 執行階段的原生路徑。  
  
```  
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
 [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)   
 [工作參考](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [ (WPF) 建立 WPF 應用程式 ](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
