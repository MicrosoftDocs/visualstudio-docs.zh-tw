---
title: MergeLocalizationDirectives 工作 | Microsoft Docs
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
ms.openlocfilehash: 9c7699afeb09604a437aad091f9aaf9ce624d33e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633495"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives 工作

該<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives>任務將一個或多個 XAML 二進位格式檔的當地語系化屬性和注釋合併到整個程式集的單個檔中。

## <a name="task-parameters"></a>工作參數

| 參數 | 描述 |
|------------------------------| - |
| `GeneratedLocalizationFiles` | 必需**的 ITaskItem]** 參數。<br /><br /> 以 XAML 二進位格式指定單個檔的當地語系化指令檔案清單。 |
| `OutputFile` | 必要的 **String** 輸出參數。<br /><br /> 指定編譯的當地語系化指示詞組件的輸出路徑。 |

## <a name="remarks"></a>備註

您可以將當地語系化屬性和注釋添加到 XAML 內容。 借助 Windows 演示文稿基礎 （WPF） 當地語系化支援，可以剝離當地語系化屬性和注釋，並將它們放在與生成的程式集分開的 *.loc*檔中。 您可以使用 **LocalizationPropertyStorage** 屬性來執行此動作。 如需當地語系化屬性和註解，以及 **LocalizationPropertyStorage** 的詳細資訊，請參閱[當地語系化屬性和註解](/dotnet/framework/wpf/advanced/localization-attributes-and-comments)。

## <a name="example"></a>範例

下面的示例將多個 XAML 二進位格式檔的當地語系化注釋合併到單個 *.loc*檔中。

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

## <a name="see-also"></a>另請參閱

- [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild 任務引用](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [MSBuild 任務引用](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
