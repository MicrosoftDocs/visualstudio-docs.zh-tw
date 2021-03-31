---
title: 建立專案範本
description: 瞭解如何在 Visual Studio 中使用 [匯出範本] 嚮導和其他方法來建立專案範本。
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: a823d6a519da286e5c6df8947d64934a244c1985
ms.sourcegitcommit: 9c831a7f39e5b3e3c5db000b2545715bf12225f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2021
ms.locfileid: "105933767"
---
# <a name="how-to-create-project-templates"></a>如何：建立專案範本

本主題示範如何使用 [匯出範本精靈] 建立範本，此精靈會將您的範本封裝在 *.zip* 檔案中。

## <a name="use-the-export-template-wizard"></a>使用 [匯出範本精靈]

1. 建立專案。

    > [!NOTE]
    > 在命名將會是範本來源的專案時，請您只使用有效的識別項字元。 否則，從範本建立的專案會發生編譯錯誤。 如需有效識別碼字元的詳細資訊，請參閱[宣告項目名稱 (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) 或 [識別碼 (C++)](/cpp/cpp/identifiers-cpp)。 或者，您也可以使用[範本參數](../ide/template-parameters.md)為類別和命名空間使用「安全」的名稱。

2. 編輯專案，直到它準備好匯出成範本。 例如，您可能想要編輯程式碼檔案，指出應該執行參數取代的地方。 請參閱[如何：替代範本中的參數](../ide/how-to-substitute-parameters-in-a-template.md)。

3. 選擇 [ **專案** ] 功能表上的 [ **匯出範本**]。

   [ **匯出範本]** 隨即開啟。

4. 在 [選擇範本類型] 頁面上，選取 [專案範本]。 選取您想要匯出至範本的專案，然後選擇 [下一步]。

::: moniker range="vs-2017"

5. 在 [選取範本選項] 頁面上，輸入範本的名稱和選擇性描述、圖示和預覽影像。 這些項目會出現在 [新增專案] 對話方塊中。 選擇 [完成]。

   專案會匯出成 *.zip* 檔案並放在指定的輸出位置，且如果選取，則會匯入到 Visual Studio。

若要在 [新增專案] 對話方塊中尋找您的範本，請展開 [已安裝]，然後展開對應至 *.vstemplate* 檔案之 `ProjectType` 項目的類別。 例如，包含 `<ProjectType>CSharp</ProjectType>` 的 *.vstemplate* 檔案預設出現在 [已安裝] > [Visual C#] 下。 您可以將範本整理成專案類型的子目錄，只要在該目錄中建立資料夾，然後放入您範本的 *.zip* 檔案即可。 如需詳細資訊，請參閱[如何：尋找並整理範本](../ide/how-to-locate-and-organize-project-and-item-templates.md)。

::: moniker-end

::: moniker range=">=vs-2019"

5. 在 [選取範本選項] 頁面上，輸入範本的名稱和選擇性描述、圖示和預覽影像。 這些項目會出現在您建立新專案的對話方塊中。 選擇 [完成]。

   專案會匯出成 *.zip* 檔案並放在指定的輸出位置，且如果選取，則會匯入到 Visual Studio。

若要在您建立新專案的對話方塊中尋找範本，請依名稱或捲動清單來搜尋。 (使用者範本目前無法依據語言或專案類型來篩選。)

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>建立專案範本的其他方式

您可以將構成專案的檔案收集在一個資料夾中，然後使用合適的中繼資料建立 *.vstemplate* XML 檔案，以手動方式建立專案範本。 如需詳細資訊，請參閱[如何：以手動方式建立網站範本](../ide/how-to-manually-create-web-templates.md)。

如已安裝 Visual Studio SDK，可以使用 [VSIX 專案] 範本，將完成的範本包裝成 VSIX 檔進行部署。 如需詳細資訊，請參閱[開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)。

## <a name="see-also"></a>另請參閱

- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [如何：建立專案範本](../ide/how-to-create-item-templates.md)
- [開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)
- [自訂專案和項目範本](customizing-project-and-item-templates.md)
