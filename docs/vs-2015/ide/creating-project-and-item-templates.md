---
title: 建立專案和項目範本 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e288329637c6a6f421a5b32f19084897a31e5f22
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499502"
---
# <a name="creating-project-and-item-templates"></a>建立專案和項目範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[建立專案和項目範本](https://docs.microsoft.com/visualstudio/ide/creating-project-and-item-templates)。  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案範本和項目範本提供可重複使用的 Stub，讓使用者有一些基本的程式碼和結構可自行運用。  
  
## <a name="visual-studio-templates"></a>Visual Studio 範本  
 安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 時會安裝一些預先定義的專案範本和項目範本。 [新增專案] 對話方塊中可用的 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 和 [!INCLUDE[csprcs](../includes/csprcs-md.md)] Windows Forms 應用程式和類別庫範本，就是專案範本範例。 已安裝的項目範本位於 [新增項目] 對話方塊，並且包含程式碼檔案、XML 檔案、HTML 網頁和樣式表這類項目。  
  
 使用者可將這些範本當做起點，開始建立專案或擴充目前專案。 專案範本提供特定專案類型所需的檔案、包含標準組件參考，並設定預設專案屬性和編譯器選項。 項目範本可能只是一個有正確副檔名的空檔案，也可能是一個多檔案項目那麼複雜，例如，項目中包含原始程式碼檔案 (含有 Stub 程式碼)、設計工具資訊檔案和內嵌資源。  
  
 除了 [新增專案] 和 [新增項目] 對話方塊中已安裝的範本之外，您還可以撰寫自己的範本，或下載並使用社群所建立的範本。 如需詳細資訊，請參閱[如何：建立專案範本](../ide/how-to-create-project-templates.md)和[如何：建立項目範本](../ide/how-to-create-item-templates.md)。  
  
## <a name="contents-of-a-template"></a>範本的內容  
 所有專案範本和項目範本，不論是隨 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 一起安裝或由您建立，都以相同的原理運作且具有相似的內容。 所有範本都包含下列項目：  
  
-   使用範本時要建立的檔案。 這包括原始程式碼檔案、內嵌資源、專案檔等等。  
  
-   一個 .vstemplate 檔案。 此檔案包含的中繼資料提供必要資訊，讓 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 在 [新增專案] 和 [新增項目] 對話方塊中顯示範本，以及從範本建立專案或項目。 如需 .vstemplate 檔案的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。  
  
 當這些檔案壓縮成 .zip 檔案並放入正確的資料夾時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會自動顯示它們。 專案範本出現在 [新增專案] 對話方塊的 [我的範本] 區段中，而項目範本出現在 [新增項目] 對話方塊中。 如需範本資料夾的詳細資訊，請參閱[如何：尋找並組織範本](../ide/how-to-locate-and-organize-project-and-item-templates.md)。  
  
## <a name="starter-kits"></a>入門套件  
 入門套件是增強的範本，可以與社群的其他成員共用。 入門套件包含可編譯的程式碼範例、文件和其他資源，協助使用者經由建置實際有用的應用程式，學習新的工具和程式設計技巧。 入門套件的基本內容和程序，與範本完全相同。 如需詳細資訊，請參閱[如何：建立入門套件](../ide/how-to-create-starter-kits.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立專案範本](../ide/how-to-create-project-templates.md)   
 [如何：建立項目範本](../ide/how-to-create-item-templates.md)   
 [範本參數](../ide/template-parameters.md)   
 [自訂範本](../ide/customizing-project-and-item-templates.md)   
 [如何：建立入門套件](../ide/how-to-create-starter-kits.md)



