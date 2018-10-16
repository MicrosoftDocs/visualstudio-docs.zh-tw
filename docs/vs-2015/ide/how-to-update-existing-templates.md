---
title: 如何： 更新現有的範本 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa7c6f534756298006e07d287b118edfd4944717
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242277"
---
# <a name="how-to-update-existing-templates"></a>如何：更新現有的範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在建立範本並將檔案壓縮成 .zip 檔之後，您可能想要修改範本。 若要執行此動作，您可以手動變更範本中的檔案，或從以範本為基礎的專案中匯出新範本。  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>使用匯出範本精靈更新現有範本  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供**匯出範本**可用來更新現有範本的精靈。  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>使用匯出範本更新現有範本  
  
1.  在 [檔案]  功能表上，按一下 [新增]  及 [新增專案] 。  
  
2.  選取您想要更新中，輸入名稱和位置的暫存專案，然後按一下範本**確定**。  
  
3.  在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中修改專案。  
  
4.  在上**檔案**功能表上，按一下**匯出範本**，並使用**匯出範本**精靈來建立新的範本。  
  
5.  更新的範本壓縮成 .zip 檔之後，請刪除舊範本的 .zip 檔。  
  
## <a name="manually-updating-an-existing-template"></a>手動更新現有範本  
 您可以藉由修改壓縮 .zip 檔中的檔案，在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 以外更新現有範本。  
  
#### <a name="to-manually-update-an-existing-template"></a>手動更新現有範本  
  
1.  找出包含樣板的.zip 檔。 根據預設，此檔案位於 documents\visual Studio*版本*\My Exported Templates\\。  
  
2.  將 zip 檔解壓縮。  
  
3.  修改或刪除目前的範本檔，或將新檔案加入至範本。  
  
4.  開啟、修改和儲存.vstemplate XML 檔，以處理更新的行為或新檔案。 如需 .vstemplate 結構描述的詳細資訊，請參閱 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。 如需有關您可以參數化的原始程式檔中的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)  
  
5.  選取您的範本中的檔案上按一下滑鼠右鍵，按一下**傳送到**，然後按一下**壓縮 (zipped) 資料夾**。 您選取的檔案即會壓縮成 .zip 檔。  
  
6.  將新的 .zip 檔放在與舊 .zip 檔相同的目錄中。  
  
7.  刪除已解壓縮的樣板檔案和舊樣板 .zip 檔案。  
  
8.  啟動 （以系統管理員身分） 執行個體的開發人員命令提示字元 (在 [開始] 功能表底下**Visual Studio 2010 / Visual Studio Tools/開發人員命令提示字元**)。  
  
9. 執行下列命令：`devenv /installvstemplates`  
  
## <a name="see-also"></a>另請參閱  
 [自訂範本](../ide/customizing-project-and-item-templates.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [範本參數](../ide/template-parameters.md)   
 [如何：建立入門套件](../ide/how-to-create-starter-kits.md)



