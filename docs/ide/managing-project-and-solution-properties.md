---
title: 管理專案和解決方案屬性
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96581fbaff9c2ddc85fbb92d73096f2a369d4c7b
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746308"
---
# <a name="manage-project-and-solution-properties"></a>管理專案和解決方案屬性

專案具有控管編譯、偵錯、測試和部署各個層面的屬性。 有些屬性是所有專案類型通用的，有些則是特定語言或平台特有的。 在 [方案總管] 的專案節點上按一下滑鼠右鍵並選擇 [屬性]，或在功能表列 [快速啟動] 的搜尋方塊中鍵入「屬性」，即可存取專案屬性。

![[專案] 內容功能表](../ide/media/vs2015_proj_prop_menu.gif)

在專案樹狀結構本身，.NET 專案也可能具有屬性節點。

![方案總管樹狀目錄中的 [屬性] 節點](../ide/media/vs2015_props_se.png)

## <a name="project-properties"></a>專案屬性

專案屬性會組織成群組，且每個群組都有自己的屬性頁。 不同的語言和專案類型可能有不同的頁面。

### <a name="c-visual-basic-and-f-projects"></a>C#、Visual Basic 和 F# 專案

C#、Visual Basic 和 F# 專案的屬性是公開在 [專案設計工具] 中。 下圖顯示 C# 中 WPF 專案的 [建置] 屬性頁：

![Visual Studio 專案設計工具](../ide/media/vs2015_proppage_build.png)

如需 [專案設計工具] 中每個屬性頁的詳細資訊，請參閱[專案屬性參考](../ide/reference/project-properties-reference.md)。

> [!TIP]
> 方案有一些屬性，專案項目也有；您可以在[屬性視窗](../ide/reference/properties-window.md)中存取這些屬性，而非 [專案設計工具]。

### <a name="c-and-javascript-projects"></a>C++ 和 JavaScript 專案

C++ 和 JavaScript 專案具有不同的使用者介面來管理專案屬性。 下圖顯示 C++ 專案屬性頁 (JavaScript 的專案屬性頁也很類似)：

![Visual C&#43;&#43; 專案屬性](../ide/media/vs2015_projprops_cpp.png)

如需 C++ 專案屬性的資訊，請參閱[使用專案屬性 (C++)](/cpp/ide/working-with-project-properties)。 如需 JavaScript 屬性的詳細資訊，請參閱 [JavaScript、屬性頁](../ide/reference/property-pages-javascript.md)。

## <a name="solution-properties"></a>解決方案屬性

若要存取方案上的屬性，請以滑鼠右鍵按一下方案總管中的方案節點，然後選擇 [屬性]。 在對話方塊中，您可以設定 [偵錯] 或 [發行] 組建的專案組態、在按 **F5** 時選擇哪些專案應該要作為啟始專案，以及設定程式碼分析選項。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md)
