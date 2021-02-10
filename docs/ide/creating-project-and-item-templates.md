---
title: 適用於專案和檔案的範本
description: 瞭解專案和專案範本如何提供可重複使用的存根，讓使用者有一些基本的程式碼和結構。
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: e5a3a555a9c0674c70e93ec557416c05d282fbcf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956811"
---
# <a name="project-and-item-templates"></a>專案範本與項目範本

專案範本與項目範本提供可重複使用的虛設常式，讓使用者有一些基本的程式碼和結構可依其目的來自行自訂。

## <a name="visual-studio-templates"></a>Visual Studio 範本

安裝 Visual Studio 時會安裝一些預先定義的專案範本和項目範本。 這些範本 (例如 **ASP.NET Web 應用程式** 和 **類別庫** 範本) 可讓您在建立新專案時選擇。 項目範本 (例如程式碼檔案、XML 檔案、HTML 頁面和樣式表) 會顯示在 [新增項目] 對話方塊中。

使用者可將這些範本當作起點開始建立專案，或擴充現有的專案。 專案範本提供特定專案類型所需的檔案、包含標準組件參考，並設定預設專案屬性和編譯器選項。 項目範本複雜多變，從有特定副檔名的單一空檔案，到具有虛設常式程式碼的多個原始程式碼檔案、設計工具資訊檔案和內嵌資源，都有可能。

您可以使用已安裝範本、撰寫自己的自訂範本，或下載並使用社群所建立的範本。 如需詳細資訊，請參閱 [如何：建立專案範本](../ide/how-to-create-project-templates.md) 和 [如何：建立專案範本](../ide/how-to-create-item-templates.md)。

## <a name="contents-of-a-template"></a>範本的內容

所有專案範本和項目範本，不論是隨 Visual Studio 一起安裝或由您建立，都以相同的原理運作且具有相似的內容。 所有範本都包含下列項目：

- 使用範本時要建立的檔案。 這些檔案包含原始程式碼檔案、內嵌資源、專案檔等等。

::: moniker range="vs-2017"

- .vstemplate 檔案，包含從 [新增專案] 和 [新增項目] 視窗中從範本建立專案或項目以及顯示範本所需的中繼資料。

::: moniker-end

::: moniker range=">=vs-2019"

- .vstemplate 檔案，包含從 [新增專案] 頁面或 [新增項目] 對話方塊中從範本建立專案或項目以及顯示範本所需的中繼資料。

::: moniker-end

   如需 *.vstemplate* 檔案的詳細資訊，請參閱 [範本標籤](template-tags.md)和 [範本參數](../ide/template-parameters.md)。

當這些檔案壓縮成 .zip 檔案並放入正確的資料夾時，Visual Studio 會自動在下列位置顯示它們：

::: moniker range="vs-2017"

- 專案範本會出現在 [新增專案] 視窗。

::: moniker-end

::: moniker range=">=vs-2019"

- 專案範本會出現在 [建立新專案] 頁面。

::: moniker-end

- 項目範本會出現在 [新增項目] 視窗。

如需範本資料夾的詳細資訊，請參閱 [如何：尋找並整理範本](../ide/how-to-locate-and-organize-project-and-item-templates.md)。

## <a name="see-also"></a>另請參閱

- [如何：建立專案範本](../ide/how-to-create-project-templates.md)
- [如何：建立專案範本](../ide/how-to-create-item-templates.md)
- [範本標籤](template-tags.md)
- [範本參數](../ide/template-parameters.md)
- [自訂範本](../ide/customizing-project-and-item-templates.md)
- [Visual Studio 範本中的 NuGet 套件](/nuget/visual-studio-extensibility/visual-studio-templates)
