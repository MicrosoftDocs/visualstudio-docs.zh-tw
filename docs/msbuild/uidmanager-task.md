---
title: UidManager 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c4e8c5ccae37aba0f287e2c2f9e29ab36371846
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62938656"
---
# <a name="uidmanager-task"></a>UidManager 工作
<xref:Microsoft.Build.Tasks.Windows.UidManager> 工作會檢查、更新或移除唯一識別碼 (UID)，以將來源 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案中包含的所有 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 項目當地語系化。

## <a name="task-parameters"></a>工作參數

| 參數 | 說明 |
|-------------------------| - |
| `IntermediateDirectory` | 選擇性的 **String** 參數。<br /><br /> 指定用於備份來源 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案的目錄，該檔案是由 **MarkupFiles** 參數指定。 |
| `MarkupFiles` | 必要的 **ITaskItem[]** 參數。<br /><br /> 指定要包含的來源 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案以進行 UID 檢查、更新或移除。 |
| `Task` | 必要的 **String** 參數。<br /><br /> 指定您想要執行的 UID 管理工作。 有效的選項為 **Check**、**Update** 或 **Remove**。 |

## <a name="example"></a>範例
 下列範例會使用 <xref:Microsoft.Build.Tasks.Windows.UidManager> 工作來檢查指定來源 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案是否包含具有正確 UID 的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 項目。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UidManagerTask">
    <UidManager
      Task="Check"
      MarkupFiles="Page1.xaml;Page2.xaml"
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />
  </Target>
</Project>
```

## <a name="see-also"></a>另請參閱
- [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)
- [工作參考](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [如何：將應用程式當地語系化](/dotnet/framework/wpf/advanced/how-to-localize-an-application)