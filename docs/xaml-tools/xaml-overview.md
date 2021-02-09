---
title: XAML 概觀
description: 瞭解 XAML 和 XAML 程式碼編輯器的基本資訊，以及 Visual Studio 中的 XAML 設計工具工具。
ms.custom: SEO-VS-2020
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 6f315573b24989e6ad3a3d451de372430b72f70f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931187"
---
# <a name="overview-of-xaml"></a>XAML 概觀

Extensible Application Markup Language (XAML) 是一種以 XML 為基礎的宣告式語言。 XAML 在下列類型的應用程式中廣泛用來建置使用者介面：

- [Windows Presentation Foundation (WPF) 應用程式](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [通用 Windows 平台 (UWP) 應用程式](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 應用程式](/xamarin/xamarin-forms/xaml/)

下列 XAML 程式碼定義了一個簡單的按鈕控制項。

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML 也用來在 [Windows WorkFlow Foundation (WF) 應用程式](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml)中定義工作流程。

## <a name="xaml-code-editor"></a>XAML 程式碼編輯器

Visual Studio IDE 中的 [XAML 程式碼編輯器](xaml-code-editor.md) 包含為 Windows 平臺和 XAMARIN 建立 WPF 和 UWP 應用程式所需的所有工具。 雖然 IDE (Visual Studio 中的整合式開發環境) 有許多功能可供您用來開發適用于其他平臺的應用程式，但也有一些 XAML 特有的功能。

## <a name="xaml-designer"></a>XAML 設計工具

Visual Studio 和 Blend for Visual Studio 提供的 [XAML 設計工具](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) ，可協助您建立適用于 WPF、UWP 和 Xamarin 應用程式的使用者介面 (UI) 。 您可以從 [工具箱] 或 [資產] 視窗拖曳控制項，然後在 [屬性] 視窗中設定屬性。 當您這樣做時，Visual Studio 和 Blend for Visual Studio 建立對應的 XAML 程式碼。 如果您偏好直接編輯 XAML 程式碼，您也可以那樣做。

## <a name="whats-new"></a>最新消息

如需最新資訊，請參閱下列資源：

- **[Visual Studio 2019 16.7 版 Preview 1 blog 文章中的 XAML 工具改進](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)**
- Visual Studio 2019 blog 文章中 **[XAML 開發人員工具的新功能](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)**
- YouTube **[Visual Studio video 中的新 XAML 功能](https://youtu.be/yI9OyA4ZM2E)**

## <a name="see-also"></a>另請參閱

- [WPF 應用程式中的 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP 應用程式中的 XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 應用程式中的 XAML](/xamarin/xamarin-forms/xaml/)
