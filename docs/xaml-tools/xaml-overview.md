---
title: XAML 概觀
ms.date: 07/31/2019
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a5f366e81a0ef3c13c3ca1c39ccc3bf44257b6e7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592901"
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

## <a name="xaml-designer"></a>XAML 設計工具

Visual Studio 和 Blend for Visual Studio 提供「XAML 設計工具」，可協助您建置 WPF、UWP 及 Xamarin.Forms 應用程式的使用者介面 (UI)。 您可以從 [工具箱] 或 [資產] 視窗拖曳控制項，然後在 [屬性] 視窗中設定屬性。 當您執行這些動作時，Visual Studio 和 Blend for Visual Studio 會建立對應的 XAML 程式碼。 如果您偏好直接編輯 XAML 程式碼，您也可以那樣做。

本文件集內的文章探討 Visual Studio 和 Blend for Visual Studio 中的「XAML 設計工具」。

## <a name="see-also"></a>請參閱

- [WPF 應用程式中的 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP 應用程式中的 XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 應用程式中的 XAML](/xamarin/xamarin-forms/xaml/)
