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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37692c541fb2a6e9b2ccf61083dd383e56a79766
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631519"
---
# <a name="uidmanager-task"></a>UidManager 工作

任務<xref:Microsoft.Build.Tasks.Windows.UidManager>檢查、更新或刪除唯一識別碼 （UiD）， 以便當地語系化源 XAML 檔中包含的所有 XAML 元素。

## <a name="task-parameters"></a>工作參數

| 參數 | 描述 |
|-------------------------| - |
| `IntermediateDirectory` | 可選**字串**參數。<br /><br /> 指定用於備份標記檔參數指定的源 XAML**檔的**目錄。 |
| `MarkupFiles` | 必需**的 ITaskItem]** 參數。<br /><br /> 指定要包括的用於 UID 檢查、更新或刪除的源 XAML 檔。 |
| `Task` | 必要的 **String** 參數。<br /><br /> 指定您想要執行的 UID 管理工作。 有效的選項為 **Check**、**Update** 或 **Remove**。 |

## <a name="example"></a>範例

 下面的示例使用<xref:Microsoft.Build.Tasks.Windows.UidManager>任務來檢查指定的源 XAML 檔包含具有適當 UiD 的 XAML 元素。

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
- [任務引用](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [任務引用](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [如何：當地語系化應用程式](/dotnet/framework/wpf/advanced/how-to-localize-an-application)