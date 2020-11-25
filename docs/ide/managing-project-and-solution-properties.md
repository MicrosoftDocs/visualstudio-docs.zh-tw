---
title: 管理專案和解決方案屬性
description: 瞭解如何在 Visual Studio 中管理專案屬性和方案屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b7b89588e778a142e7dd49e1a3051a9aa188ff1
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871388"
---
# <a name="manage-project-and-solution-properties"></a>管理專案和解決方案屬性

專案具有控管編譯、偵錯、測試和部署各個層面的屬性。 有些屬性是所有專案類型通用的，有些則是特定語言或平台特有的。 以滑鼠右鍵按一下 [方案總管] 的專案節點，然後選擇 [屬性]，或在功能表列的搜尋方塊中鍵入 **屬性**，然後從結果中選擇 [屬性視窗]。

![專案操作功能表](../ide/media/vs2015_proj_prop_menu.gif)

在專案樹狀結構本身，.NET 專案也可能具有屬性節點。

![方案總管樹狀目錄中的 [屬性] 節點](../ide/media/vs2015_props_se.png)

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[管理方案和專案屬性 (Visual Studio for Mac)](/visualstudio/mac/managing-solutions-and-project-properties)。

## <a name="project-properties"></a>專案屬性

專案屬性會組織成群組，且每個群組都有自己的屬性頁。 不同的語言和專案類型可能有不同的頁面。

### <a name="c-visual-basic-and-f-projects"></a>C#、Visual Basic 和 F# 專案

在 c #、Visual Basic 和 F # 專案中，屬性會在 [ **專案設計** 工具] 中公開。 下圖顯示 c # 中 WPF 專案的 [ **組建** ] 屬性頁：

![Visual Studio 專案設計工具](../ide/media/vs2015_proppage_build.png)

如需 [ **專案設計** 工具] 中每個屬性頁的詳細資訊，請參閱 [專案屬性參考](../ide/reference/project-properties-reference.md)。

> [!TIP]
> 方案有幾個屬性，而專案專案則為;這些屬性可在 [屬性視窗](../ide/reference/properties-window.md)中存取，而不是在 **專案設計** 工具中存取。

### <a name="c-and-javascript-projects"></a>C++ 和 JavaScript 專案

C++ 和 JavaScript 專案具有不同的使用者介面來管理專案屬性。 下圖顯示 C++ 專案屬性頁 (JavaScript 的專案屬性頁也很類似)：

![Visual C&#43;&#43; 專案屬性](../ide/media/vs2015_projprops_cpp.png)

如需 C++ 專案屬性的資訊，請參閱[使用專案屬性 (C++)](/cpp/build/working-with-project-properties)。 如需 JavaScript 屬性的詳細資訊，請參閱 [javascript 的屬性頁](../ide/reference/property-pages-javascript.md)。

## <a name="solution-properties"></a>解決方案屬性

若要存取方案上的屬性，請以滑鼠右鍵按一下方案總管中的方案節點，然後選擇 [屬性]。 在對話方塊中，您可以設定 **Debug** 或 **Release** 組建的專案設定，在按下 **F5** 時選擇哪些專案應該是啟始專案，以及設定程式碼分析選項。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md)
- [管理方案和專案屬性 (Visual Studio for Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
