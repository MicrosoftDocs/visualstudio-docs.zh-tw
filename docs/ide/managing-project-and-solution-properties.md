---
title: 管理專案和解決方案屬性
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3d5b1150c67eeb5d47741ed9331dcdc11a82582
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714953"
---
# <a name="manage-project-and-solution-properties"></a>管理專案和解決方案屬性

專案具有控管編譯、偵錯、測試和部署各個層面的屬性。 有些屬性是所有專案類型通用的，有些則是特定語言或平台特有的。 以滑鼠右鍵按一下 [方案總管]  的專案節點，然後選擇 [屬性]  ，或在功能表列的搜尋方塊中鍵入**屬性**，然後從結果中選擇 [屬性視窗]  。

![[專案] 內容功能表](../ide/media/vs2015_proj_prop_menu.gif)

在專案樹狀結構本身，.NET 專案也可能具有屬性節點。

![方案總管樹狀目錄中的 [屬性] 節點](../ide/media/vs2015_props_se.png)

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[管理方案和專案屬性 (Visual Studio for Mac)](/visualstudio/mac/managing-solutions-and-project-properties)。

## <a name="project-properties"></a>專案屬性

專案屬性會組織成群組，且每個群組都有自己的屬性頁。 不同的語言和專案類型可能有不同的頁面。

### <a name="c-visual-basic-and-f-projects"></a>C#、Visual Basic 和 F# 專案

C#、Visual Basic 和 F# 專案的屬性是公開在 [專案設計工具]  中。 下圖顯示 C# 中 WPF 專案的 [建置]  屬性頁：

![Visual Studio 專案設計工具](../ide/media/vs2015_proppage_build.png)

如需 [專案設計工具]  中每個屬性頁的詳細資訊，請參閱[專案屬性參考](../ide/reference/project-properties-reference.md)。

> [!TIP]
> 方案有一些屬性，專案項目也有；您可以在[屬性視窗](../ide/reference/properties-window.md)中存取這些屬性，而非 [專案設計工具]  。

### <a name="c-and-javascript-projects"></a>C++ 和 JavaScript 專案

C++ 和 JavaScript 專案具有不同的使用者介面來管理專案屬性。 下圖顯示 C++ 專案屬性頁 (JavaScript 的專案屬性頁也很類似)：

![Visual C&#43;&#43; 專案屬性](../ide/media/vs2015_projprops_cpp.png)

如需 C++ 專案屬性的資訊，請參閱[使用專案屬性 (C++)](/cpp/build/working-with-project-properties)。 如需 JavaScript 屬性的詳細資訊，請參閱 [JavaScript、屬性頁](../ide/reference/property-pages-javascript.md)。

## <a name="solution-properties"></a>解決方案屬性

若要存取方案上的屬性，請以滑鼠右鍵按一下方案總管  中的方案節點，然後選擇 [屬性]  。 在對話方塊中，您可以設定 [偵錯]  或 [發行]  組建的專案組態、在按 **F5** 時選擇哪些專案應該要作為啟始專案，以及設定程式碼分析選項。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md)
- [管理方案和專案屬性 (Visual Studio for Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
