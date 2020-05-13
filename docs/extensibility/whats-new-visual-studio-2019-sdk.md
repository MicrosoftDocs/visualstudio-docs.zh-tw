---
title: 視覺工作室 2019 SDK 中的新增功能 |微軟文件
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740407"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Visual Studio 2019 SDK 的新功能

Visual Studio SDK 具有以下可視化工作室 2019 的新功能和更新功能。

## <a name="synchronously-autoloaded-extensions-warning"></a>同步自動載入延伸警告

如果使用者的已安裝擴展在啟動時同步自動載入,則用戶現在將看到一條警告。 您可以在[同步自動載入擴展](synchronously-autoloaded-extensions.md)處瞭解有關警告的更多資訊。

## <a name="single-unified-visual-studio-sdk"></a>單一、統一的視覺工作室 SDK

現在,您可以通過單個 NuGet 包[Microsoft](https://www.nuget.org/packages/microsoft.visualstudio.sdk)獲取所有 Visual Studio SDK 資產。

## <a name="editor-registration-enhancements"></a>編輯器註冊增強功能

自創建以來,Visual Studio 一直支援自定義編輯器註冊,其中編輯器可以聲明其對特定擴展(例如 .xaml 和 .rc)的關聯性,或者它適用於任何擴展 (.*)。 從 Visual Studio 2019 版本 16.1 開始,我們擴大了對編輯器註冊的支援。

### <a name="filenames"></a>檔案名稱

除了註冊對特定檔擴展名的支援之外,編輯器還可以通過將新`ProvideEditorFilename`屬性應用於編輯器的包來註冊它支援特定的檔名。

例如,支援所有 .json 檔案的編輯器會將`ProvideEditorExtension`此屬性 應用於其包:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

從 16.1 開始,如果 MyEditor 僅支援幾個眾所周知的 .json`ProvideEditorFilename`檔,則可以將這些 屬性應用於其包:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

編輯器可以註冊一個或多個 UIContext,這些 UIContext 表示啟用時。 UIContext 通過將`ProvideEditorUIContextAttribute`的一個或多個實例應用於註冊編輯器的包來註冊。

若編輯器已註冊 UIContext:

- 如果打開具有給定擴展名的檔時,其註冊的 UIContext 中至少有一個處於活動狀態,則編輯器將包含在編輯器搜尋中。
- 如果未註冊任何 UIContext 處於活動狀態,則編輯器中不包括編輯器。

如果編輯器不註冊任何 UIContext,則它始終包含在該擴展的編輯器搜尋中。

例如,如果編輯器僅在打開 C# 專案時可用,它`ProvideEditorUIContext`可以透過應用程式 屬性來聲明此關聯:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
