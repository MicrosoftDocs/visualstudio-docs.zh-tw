---
title: 適用於專案和檔案的範本
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f4c63ab9cfe055d5e1b5a9deeae29ed49b277e9a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006791"
---
# <a name="project-and-item-templates"></a>專案範本與項目範本

專案範本與項目範本提供可重複使用的虛設常式，讓使用者有一些基本的程式碼和結構可依其目的來自行自訂。

## <a name="visual-studio-templates"></a>Visual Studio 範本

安裝 Visual Studio 時會安裝一些預先定義的專案範本和項目範本。 例如，[新增專案] 對話方塊中顯示的 Visual Basic 和 C# **Windows Forms 應用程式**以及**類別庫**範本，就是專案範本。 項目範本會顯示在 [新增項目] 對話方塊中，並且包含程式碼檔案、XML 檔案、HTML 網頁和樣式表等項目。

使用者可將這些範本當作起點開始建立專案，或擴充現有的專案。 專案範本提供特定專案類型所需的檔案、包含標準組件參考，並設定預設專案屬性和編譯器選項。 項目範本複雜多變，從有特定副檔名的單一空檔案，到具有虛設常式程式碼的多個原始程式碼檔案、設計工具資訊檔案和內嵌資源，都有可能。

您可以使用 [新增專案] 和 [新增項目] 對話方塊中的已安裝範本、撰寫自己的範本，或下載並使用社群所建立的範本。 如需詳細資訊，請參閱[＜How to：建立專案範本](../ide/how-to-create-project-templates.md)和[如何：建立項目範本](../ide/how-to-create-item-templates.md)。

## <a name="contents-of-a-template"></a>範本的內容

所有專案範本和項目範本，不論是隨 Visual Studio 一起安裝或由您建立，都以相同的原理運作且具有相似的內容。 所有範本都包含下列項目：

- 使用範本時要建立的檔案。 這些檔案包含原始程式碼檔案、內嵌資源、專案檔等等。

- 一個 .vstemplate 檔案包含 [新增專案] 和 [新增項目] 對話方塊中顯示範本所需的中繼資料，以及從範本建立專案或項目。 如需 .vstemplate 檔案的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。

當這些檔案壓縮成 .zip 檔案並放入正確的資料夾時，Visual Studio 會自動在下列位置顯示它們：

- 專案範本會出現在 [新增專案] 對話方塊中。

- 項目範本會出現在 [新增項目] 對話方塊中。

如需範本資料夾的詳細資訊，請參閱[如何：尋找並整理範本](../ide/how-to-locate-and-organize-project-and-item-templates.md)。

## <a name="see-also"></a>另請參閱

- [如何：建立專案範本](../ide/how-to-create-project-templates.md)
- [如何：建立項目範本](../ide/how-to-create-item-templates.md)
- [範本參數](../ide/template-parameters.md)
- [自訂範本](../ide/customizing-project-and-item-templates.md)
- [Visual Studio 範本中的 NuGet 套件](/nuget/visual-studio-extensibility/visual-studio-templates)