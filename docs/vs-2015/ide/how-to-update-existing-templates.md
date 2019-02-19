---
title: HOW TO：更新現有的範本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5b1ffd20fb33048427ba4cacdbbd9360313db089
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771109"
---
# <a name="how-to-update-existing-templates"></a>如何：更新現有的範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在建立範本並將檔案壓縮成 .zip 檔之後，您可能想要修改範本。 若要執行此動作，您可以手動變更範本中的檔案，或從以範本為基礎的專案中匯出新範本。  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>使用匯出範本精靈更新現有範本  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供可用來更新現有範本的 [匯出範本] 精靈。  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>使用匯出範本更新現有範本  
  
1.  在 [檔案]  功能表上，按一下 [新增]  及 [新增專案] 。  
  
2.  選取您想要更新的範本，輸入暫存專案的名稱和位置，然後按一下 [確定]。  
  
3.  在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中修改專案。  
  
4.  在 [檔案] 功能表上按一下 [匯出範本]，並使用 [匯出範本] 精靈建立新的範本。  
  
5.  更新的範本壓縮成 .zip 檔之後，請刪除舊範本的 .zip 檔。  
  
## <a name="manually-updating-an-existing-template"></a>手動更新現有範本  
 您可以藉由修改壓縮 .zip 檔中的檔案，在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 以外更新現有範本。  
  
#### <a name="to-manually-update-an-existing-template"></a>手動更新現有範本  
  
1.  找出包含樣板的.zip 檔。 根據預設，此檔案位於 \My Documents\Visual Studio <版本>\My Exported Templates\\ 中。  
  
2.  將 zip 檔解壓縮。  
  
3.  修改或刪除目前的範本檔，或將新檔案加入至範本。  
  
4.  開啟、修改和儲存.vstemplate XML 檔，以處理更新的行為或新檔案。 如需 .vstemplate 結構描述的詳細資訊，請參閱 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。 如需您可以在來源檔案中參數化哪些項目的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)  
  
5.  在範本中選取檔案，按一下滑鼠右鍵，按一下 [傳送到]，然後按一下 [壓縮的 (zipped) 資料夾]。 您選取的檔案即會壓縮成 .zip 檔。  
  
6.  將新的 .zip 檔放在與舊 .zip 檔相同的目錄中。  
  
7.  刪除已解壓縮的樣板檔案和舊樣板 .zip 檔案。  
  
8.  啟動 (以系統管理員身分) 開發人員命令提示字元的執行個體 (位於 [開始] 功能表上的 [Visual Studio 2010 / Visual Studio Tools/開發人員命令提示字元] 下)。  
  
9. 執行下列命令：`devenv /installvstemplates`  
  
## <a name="see-also"></a>請參閱  
 [自訂範本](../ide/customizing-project-and-item-templates.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [範本參數](../ide/template-parameters.md)   
 [如何：建立入門套件](../ide/how-to-create-starter-kits.md)
