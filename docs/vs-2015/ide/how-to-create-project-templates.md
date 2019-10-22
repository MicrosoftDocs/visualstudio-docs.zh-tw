---
title: 如何：建立專案範本 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f358d5b95349fe99b2a2e01df5158d2c0aa10a11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668056"
---
# <a name="how-to-create-project-templates"></a>如何：建立專案範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此程序可讓您使用 [匯出範本精靈] 建立範本，此精靈會將您的範本封裝在 .zip 檔案中。 您也可以使用 [匯出範本精靈] 延伸模組，或是使用 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 中包含的範本，以 VSIX 檔案格式建立範本以改進部署，也可以手動建立範本。

### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>使用標準 [匯出範本精靈] 建立自訂專案範本

1. 建立專案。

    > [!NOTE]
    > 在命名將會是範本來源的專案時，請您只使用有效的識別項字元。 從名稱含有無效字元之專案所匯出的範本，可能會導致未來根據該範本的專案發生編譯錯誤。 如需有效識別項字元的詳細資訊，請參閱[宣告項目名稱](https://msdn.microsoft.com/library/09d8843b-c0dc-4afe-9dab-87c439a69e66)。

2. 編輯專案，直到它準備好匯出成範本。

3. 適當地編輯程式碼檔案，指出要執行參數取代的地方。 如需參數取代的詳細資訊，請參閱[如何：替代範本中的參數](../ide/how-to-substitute-parameters-in-a-template.md)。

4. 按一下 [檔案] 功能表上的 [匯出範本]。 [匯出範本精靈] 隨即開啟。

5. 按一下 [專案範本]。

6. 如果您目前的方案中有多個專案，請選取您想要匯出至範本的專案。

7. 按 [ **下一步**]。

8. 選取範本的圖示和預覽影像。 這些會出現在 [新增專案] 對話方塊。

9. 輸入範本名稱及描述。

10. 按一下 [ **完成**]。 您的專案會匯出成 .zip 檔案並放在指定的輸出位置，且如果選取，則會匯入到 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。

     如果您已安裝 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]，可以使用 [VSIX 專案] 範本，將完成的範本包裝成 .vsix 檔以便部署。 如需詳細資訊，請參閱[開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)。

## <a name="see-also"></a>請參閱
 [建立專案和專案範本](../ide/creating-project-and-item-templates.md)[如何：建立專案範本](../ide/how-to-create-item-templates.md)
