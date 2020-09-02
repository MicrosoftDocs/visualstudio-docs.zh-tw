---
title: 將使用案例連結至檔和圖表 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c713759a8ea75eed3048469327f962668efa4f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657645"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>將使用案例連結到文件與圖表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以將使用案例圖中的使用案例連結至另一個圖表或文件。 例如，您可以將使用案例連結至下列圖表和文件：

- 循序圖，可顯示如何透過使用者與系統或其主要元件之間的互動來實現使用案例的目標。

- 活動圖，可顯示執行使用案例時，使用者和系統或其主要元件的詳細動作。

- OneNote 頁面或段落，可詳述使用案例。

- Word 文件或 PowerPoint 簡報，可詳述使用案例。 您可以將這類文件保留在方案或您的小組可存取的位置中，例如 SharePoint 網站。

  若要將使用案例連結至文件，您可以在使用案例圖上建立成品，並將使用案例連接至成品。 您可以在成品的屬性中設定其他圖表或文件的檔案路徑。 按兩下成品時，即會開啟其他圖表或文件。

  您可以將想要數目的成品連線至每個使用案例。 您也可以將成品連結至使用案例圖上其他類型的項目。

### <a name="to-open-a-document-associated-with-an-artifact"></a>開啟與成品相關聯的文件

- 在使用案例圖中，按兩下成品圖形。

     即會開啟相關聯的文件。

### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>將使用案例連結至相同方案中的圖表或檔案

1. 繪製圖表 (例如循序圖或活動圖) 說明該使用案例的情節。

2. 回到使用案例圖。

3. 將此圖表或檔案從 [方案總管] 拖曳至該使用案例圖的空白部分。

4. 使用相依性從成品連接到使用**案例。**

### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>連結至方案檔 (例如 Word 文件或 PowerPoint 簡報)

1. 將文件加入方案。

    1. 將 Word 文件移至與此方案相同的 Windows 資料夾。

    2. 在方案總管中，以滑鼠右鍵按一下方案，指向 [ **加入**]，然後按一下 [ **現有專案**]。

    3. 流覽至 Word 檔，然後按一下 [ **新增**]。

         該 Word 文件會出現在 [方案總管] 的方案資料夾中。

2. 將此 Word 文件從 [方案總管] 拖曳至該使用案例圖的空白部分。

     新的成品隨即出現。

3. 使用相依性從成品連接到使用**案例。**

### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>連結至共用文件、OneNote 項目或網頁

1. 取得此共用項目的 URL。 例如，這可以是一開始是 ' ' 的網路檔案路徑，或是開頭為 ' \\ \\ HTTP://' 的網頁或 Sharepoint URL，或是 onenote 區段、頁面或段落開頭為 ' onenote： ' 的連結。

2. 在 [工具箱] 中 **，按一下 [成品]，然後** 按一下使用案例圖。

3. 選取新的成品之後，請將 URL 輸入或貼到 **超連結** 屬性。

    > [!NOTE]
    > 如果您想要提供檔案路徑，最好是在一般工作區中選擇檔案， (從 ' \\ \\ ' ) 開始，或 Visual Studio 方案內的檔案。 這確保檔案路徑在另一個小組成員的電腦上或移動方案時也仍然有效。 若要將檔（例如 Word 檔）加入至方案，請以滑鼠右鍵按一下方案總管中的方案，指向 [ **加入** ]，然後按一下 [ **現有專案**]。

## <a name="see-also"></a>另請參閱
 [Uml 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md) [Uml 使用案例圖：指導方針](../modeling/uml-use-case-diagrams-guidelines.md)[編輯 uml 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)[為您的應用程式建立模型](../modeling/create-models-for-your-app.md)
