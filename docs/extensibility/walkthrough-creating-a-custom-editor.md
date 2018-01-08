---
title: "逐步解說： 建立自訂編輯器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9e8ea75cb96b36f885a55cbf9f174394379dc05a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-editor"></a>逐步解說： 建立自訂編輯器
VSPackage 專案範本可以在 c + + 建立簡單的自訂編輯器。  VSPackage 專案範本已不再支援 C# 或 Visual Basic 專案。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="the-visual-studio-package-project-template"></a>Visual Studio Package 專案範本  
 Visual Studio Package 專案範本位在**新專案**對話方塊 [c + + 擴充性] 資料夾中  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>若要建立 VSPackage，使用 Visual Studio Package 範本  
  
1.  使用 Visual Studio Package 範本建立專案。  
  
2.  選取**自訂編輯器**選項，然後按一下**下一步**。 **編輯器選項**頁面隨即顯示。  
  
3.  輸入您的編輯器名稱**編輯器名稱**方塊。 輸入您想要與您的編輯器相關聯的副檔名**副檔名**方塊。 您的編輯器是適用於具有這個副檔名的檔案。 的副檔名已經登錄 for Visual Studio，不適用於 Windows。 輸入您的編輯器以建立新文件的預設檔案名稱**預設檔名**方塊。  
  
4.  按一下 [完成]  ，在您指定的資料夾中建立 VSPackage。  
  
### <a name="to-test-your-custom-editor"></a>若要測試您的自訂編輯器  
  
1.  在**檔案**功能表上，指向**新增**，然後按一下 **檔案**。  
  
2.  在**已安裝的範本**窗格**新檔案**對話方塊中，選取檔案的範本，然後將檔案輸入您剛才註冊。  
  
3.  按一下**開啟**來檢視和編輯文件。  
  
     此編輯器支援剪下和貼上、 尋找和取代和開啟負載作業。  
  
## <a name="see-also"></a>請參閱  
 [VSPackage](../extensibility/internals/vspackages.md)