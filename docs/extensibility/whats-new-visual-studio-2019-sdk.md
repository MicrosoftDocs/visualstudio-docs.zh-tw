---
title: Visual Studio 2019 SDK 的新功能 |Microsoft Docs
description: Visual Studio SDK 是 Visual Studio 2019 的新功能和更新功能，包括編輯器註冊的增強功能。
ms.custom: SEO-VS-2020
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67b916826cdef939bacd906cf16f311f5f2fb30e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880589"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Visual Studio 2019 SDK 的新功能

Visual Studio SDK 具有 Visual Studio 2019 的下列新功能和更新功能。

## <a name="synchronously-autoloaded-extensions-warning"></a>同步自動載入延伸模組警告

如果任何已安裝的延伸模組在啟動時同步自動載入，使用者現在會看到警告。 您可以在 [同步自動載入延伸](synchronously-autoloaded-extensions.md)模組中深入瞭解警告。

## <a name="single-unified-visual-studio-sdk"></a>單一、統一的 Visual Studio SDK

您現在可以透過單一 NuGet 套件 [VisualStudio](https://www.nuget.org/packages/microsoft.visualstudio.sdk)取得所有 Visual Studio SDK 資產。

## <a name="editor-registration-enhancements"></a>編輯器註冊增強功能

在建立之後，Visual Studio 支援自訂編輯器註冊，讓編輯器可以針對特定的 (擴充功能（例如 .xaml 和 .rc) ）宣告其親和性，或適用于任何副檔名 (. * ) 。 從 Visual Studio 2019 16.1 版開始，我們擴大了對編輯器註冊的支援。

### <a name="filenames"></a>檔案名稱

除了註冊特定副檔名的支援之外，編輯器可以將新 `ProvideEditorFilename` 屬性套用至編輯器的封裝，以註冊支援特定的檔案名。

例如，支援所有 json 檔案的編輯器會將此 `ProvideEditorExtension` 屬性套用至其封裝：

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

從16.1 開始，如果 MyEditor 僅支援一些已知的 json 檔案，它可以改為將這些 `ProvideEditorFilename` 屬性套用至其套件：

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UICoNtexts

編輯器可以註冊一個或多個 UICoNtexts，以代表啟用的時間。 UICoNtexts 的註冊方式是將一或多個實例套用 `ProvideEditorUIContextAttribute` 至註冊編輯器的封裝。

如果編輯器已註冊 UICoNtexts：

- 當開啟具有指定副檔名的檔案時，如果其中至少一個註冊的 UICoNtexts 為作用中，編輯器就會包含在編輯器搜尋中。
- 如果未使用任何已註冊的 UICoNtexts，編輯器就不會包含在編輯器搜尋中。

如果編輯器未登錄任何 UICoNtexts，它一律會包含在編輯器搜尋該擴充功能中。

例如，如果 c # 專案開啟時，編輯器才可供使用，它可以套用屬性來宣告這個親和性 `ProvideEditorUIContext` ：

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
