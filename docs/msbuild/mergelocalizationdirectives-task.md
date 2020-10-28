---
title: MergeLocalizationDirectives 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 MergeLocalizationDirectives 工作，將 XAML 二進位格式檔案的當地語系化屬性和批註合併成單一檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97d04978a2809a4744f62f27c375efdec1e43dcc
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903872"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives 工作

此工作會將 <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> 一或多個 XAML 二進位格式檔案的當地語系化屬性和批註，合併成整個元件的單一檔案。

## <a name="task-parameters"></a>工作參數

| 參數 | 描述 |
|------------------------------| - |
| `GeneratedLocalizationFiles` | 必要的 **ITaskItem []** 參數。<br /><br /> 以 XAML 二進位格式針對個別檔案指定當地語系化指示詞檔案的清單。 |
| `OutputFile` | 必要的 **String** 輸出參數。<br /><br /> 指定編譯的當地語系化指示詞組件的輸出路徑。 |

## <a name="remarks"></a>備註

您可以將當地語系化屬性和批註加入至 XAML 內容。 利用 Windows Presentation Foundation (WPF) 當地語系化支援，您可以去除當地語系化屬性和批註，然後將它們放在與產生的元件不同的 loc 檔案中 *。* 您可以使用 **LocalizationPropertyStorage** 屬性來執行此動作。 如需當地語系化屬性和註解，以及 **LocalizationPropertyStorage** 的詳細資訊，請參閱 [當地語系化屬性和註解](/dotnet/framework/wpf/advanced/localization-attributes-and-comments)。

## <a name="example"></a>範例

下列範例會將數個 XAML 二進位格式檔案的當地語系化批註合併成單一的 *loc* 檔案。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MergeLocalizationDirectivesTask">
    <MergeLocalizationDirectives
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"
      OutputFile="obj\debug\WPFMSBuildSample.loc" />
  </Target>
</Project>
```

## <a name="see-also"></a>請參閱

- [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild 工作參考](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [MSBuild 工作參考](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
