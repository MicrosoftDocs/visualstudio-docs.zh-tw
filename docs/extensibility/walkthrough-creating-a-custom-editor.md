---
title: 逐步解說：建立自訂編輯器 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8656f14f3a6c9cd52b73ac0fdd3573d008c7aa0e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847149"
---
# <a name="walkthrough-create-a-custom-editor"></a>逐步解說：建立自訂編輯器
VSPackage 專案範本可以在 c + + 建立簡單的自訂編輯器。 VSPackage 專案範本不再支援 C# 或 Visual Basic 專案。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="the-visual-studio-package-project-template"></a>Visual Studio Package 專案範本  
 您可以找到 Visual Studio Package 專案範本**新的專案**下方的對話方塊**c + + 擴充性**資料夾。  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>若要建立 VSPackage，使用 Visual Studio 封裝範本  
  
1.  使用 Visual Studio Package 範本建立專案。  
  
2.  選取 [**自訂編輯器**選項，然後按一下**下一步]**。 **編輯器選項**頁面隨即出現。  
  
3.  輸入您的編輯器名稱**編輯器名稱** 方塊中。 輸入您想要與您的編輯器產生關聯的副檔名**副檔名** 方塊中。 您的編輯器是適用於與此延伸模組的檔案。 檔案的副檔名會註冊為 Visual Studio，不適用於 Windows。 輸入與您的編輯器建立的新文件的預設檔案名稱**預設檔名** 方塊中。  
  
4.  按一下 [完成]  ，在您指定的資料夾中建立 VSPackage。  
  
### <a name="to-test-your-custom-editor"></a>若要測試您的自訂編輯器  
  
1.  在 **檔案**功能表上，指向**新增**，然後按一下 **檔案**。  
  
2.  在 **已安裝的範本**窗格**新檔案**對話方塊方塊中，選取 檔案 範本，然後將檔案輸入您註冊。  
  
3.  按一下 **開啟**來檢視和編輯文件。  
  
     編輯器支援剪下和貼上、 尋找和取代和開啟並載入作業。  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage](../extensibility/internals/vspackages.md)