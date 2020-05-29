---
title: XAML 概觀
ms.date: 05/20/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 97f3bc7777023903d5fc38ad1bda7cde45b683b6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183479"
---
# <a name="overview-of-xaml"></a>XAML 概觀

Extensible Application Markup Language (XAML) 是一種以 XML 為基礎的宣告式語言。 XAML 在下列類型的應用程式中廣泛用來建置使用者介面：

- [Windows Presentation Foundation (WPF) 應用程式](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [通用 Windows 平臺（UWP）應用程式](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 應用程式](/xamarin/xamarin-forms/xaml/)

下列 XAML 程式碼定義了一個簡單的按鈕控制項。

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML 也用來在 [Windows WorkFlow Foundation (WF) 應用程式](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml)中定義工作流程。

## <a name="xaml-designer"></a>XAML 設計工具

Visual Studio 和 Blend for Visual Studio 提供「XAML 設計工具」，可協助您建置 WPF、UWP 及 Xamarin.Forms 應用程式的使用者介面 (UI)。 您可以從 [工具箱] 或 [資產] 視窗拖曳控制項，然後在 [屬性] 視窗中設定屬性。 當您這麼做時，Visual Studio 和 Blend for Visual Studio 建立對應的 XAML 程式碼。 如果您偏好直接編輯 XAML 程式碼，您也可以那樣做。

本文件集內的文章探討 Visual Studio 和 Blend for Visual Studio 中的「XAML 設計工具」。

## <a name="whats-new"></a>新功能

如需最新資訊，請參閱[xaml 開發人員工具的新功能 Visual Studio 2019 的](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)blog 文章、 [Visual Studio 2019 版本 16.7 Preview 1 中的 xaml 工具改善](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)和 YouTube 上 VISUAL STUDIO video 的[新 xaml 功能](https://youtu.be/yI9OyA4ZM2E)。

## <a name="see-also"></a>另請參閱

- [WPF 應用程式中的 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP 應用程式中的 XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 應用程式中的 XAML](/xamarin/xamarin-forms/xaml/)
