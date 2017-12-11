---
title: "如何：更新現有的範本 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0fffcc55953e394c5efd00b86949f04474a66111
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-update-existing-templates"></a>如何：更新現有的範本
在建立範本並將檔案壓縮成 .zip 檔之後，您可能想要修改範本。 若要執行此動作，您可以手動變更範本中的檔案，或從以範本為基礎的專案中匯出新範本。  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>使用匯出範本精靈更新現有範本  
Visual Studio 提供可用來更新現有範本的 [匯出範本精靈]。  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>使用匯出範本更新現有範本  
  
1.  開啟 [新增專案] 對話方塊，方法是選擇 [檔案]、[新增]、[專案]。  
  
2.  選取您想要更新的範本，輸入專案的名稱和位置，然後選擇 [確定]。  
  
3.  在 Visual Studio 中修改專案。  
  
4.  選擇 [專案] 功能表上的 [匯出範本]。  

    [匯出範本精靈] 隨即開啟。  

5.  遵循精靈中的指示，將範本匯出成 .zip 檔案。  

6.  刪除舊的範本 .zip 檔案。  
  
## <a name="manually-updating-an-existing-template"></a>手動更新現有範本  
您可以藉由修改壓縮 .zip 檔中的檔案，在 Visual Studio 以外更新現有範本。  
  
#### <a name="to-manually-update-an-existing-template"></a>手動更新現有範本  
  
1.  找出包含樣板的.zip 檔。 根據預設，此檔案位於 %USERPROFILE%\Documents\Visual Studio \<版本\>\My Exported Templates\.  
  
2.  將 zip 檔解壓縮。  
  
3.  修改或刪除目前的範本檔，或將新檔案加入至範本。  
  
4.  開啟、修改和儲存.vstemplate XML 檔，以處理更新的行為或新檔案。  

    如需 .vstemplate 結構描述的詳細資訊，請參閱 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。 如需關於您可以在來源檔案中參數化哪些項目的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。  
  
5.  在範本中選取檔案，按一下滑鼠右鍵，選擇 [傳送到]，然後選擇 [壓縮的 (zipped) 資料夾]。  

    您選取的檔案即會壓縮成 .zip 檔。  
  
6.  將新的 .zip 檔放在與舊 .zip 檔相同的目錄中。  
  
7.  刪除已解壓縮的樣板檔案和舊樣板 .zip 檔案。  
  
8.  啟動提升權限的開發人員命令提示字元執行個體：  

  1. 在 [開始] 功能表中，巡覽至 **Visual Studio \<版本\>**、[開發人員命令提示字元]。  

  2. 從內容 (以滑鼠右鍵按一下) 功能表中，選擇 [詳細]、[以系統管理員身分執行]。  
  
9. 執行下列命令：`devenv /installvstemplates`  
  
## <a name="see-also"></a>請參閱  
[自訂範本](../ide/customizing-project-and-item-templates.md)   
[建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
[Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
[範本參數](../ide/template-parameters.md)   
[如何：建立入門套件](../ide/how-to-create-starter-kits.md)