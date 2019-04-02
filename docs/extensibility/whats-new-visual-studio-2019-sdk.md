---
title: 什麼是 Visual Studio 2019 SDK 的新功能 |Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: daa4203ccdcbce89f1eb09efdd9433210bcbc987
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58856641"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>在 Visual Studio 2019 SDK 最新消息

Visual Studio SDK for Visual Studio 2019 具有下列全新和更新功能。

## <a name="synchronously-autoloaded-extensions-warning"></a>同步警告的應用程式擴充功能

如果有任何其已安裝的擴充功能以同步方式是在啟動應用程式，使用者現在會看到一則警告。 您可以深入了解在警告[同步應用程式擴充功能](synchronously-autoloaded-extensions.md)。

## <a name="single-unified-visual-studio-sdk"></a>單一、 統一的 Visual Studio SDK

您現在可以透過單一的 NuGet 套件來取得 Visual Studio SDK 的所有資產[Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk)。

## <a name="editor-registration-enhancements"></a>登錄編輯器增強功能

Visual Studio 已自其建立，支援的其中編輯器可以宣告特定的擴充功能 （例如.xaml 和.rc），其親和性或適合任何延伸模組的自訂編輯器註冊 (。 *)。 從 Visual Studio 2019 16.1 版本開始，我們會擴大編輯器註冊的支援。

### <a name="filenames"></a>檔案名稱

編輯器中加上或而非註冊特定副檔名的支援，可以註冊它支援特定的檔案名稱，藉由套用新`ProvideEditorFilename`屬性編輯器的封裝。

例如，支援所有的.json 檔案的編輯器會將此套用`ProvideEditorExtension`其封裝屬性：

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

開始 16.1，如果 MyEditor 只支援幾個已知的.json 檔案，它可以改為套用這些`ProvideEditorFilename`屬性至其套件：

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

編輯器可以註冊一個或多個代表啟用時的 UIContexts。 藉由套用的一或多個執行個體註冊的 UIContexts`ProvideEditorUIContextAttribute`登錄編輯程式的套件。

如果編輯器具有已註冊的 UIContexts:

- 如果至少一個已註冊的 UIContexts 為作用中具有指定副檔名的檔案開啟時，編輯器會包含在編輯器的搜尋服務中。
- 如果沒有任何已註冊的 UIContexts 為作用中，編輯器不會包含在編輯器的搜尋服務中。

如果編輯器不會註冊任何 UIContexts，它一律包含在編輯器中搜尋該延伸模組。

例如，如果編輯器時，才可以使用C#開啟專案時，它可以宣告此親和性，藉由套用`ProvideEditorUIContext`屬性：

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```