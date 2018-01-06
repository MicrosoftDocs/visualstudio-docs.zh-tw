---
title: "如何： 變更 ClickOnce 應用程式發行語言 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: "19"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 7d368f036e8a5f8599a802bb6f57eba7bc6d767d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>如何：變更 ClickOnce 應用程式的發行語言
發行時[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式，在安裝語言與您的開發電腦的文化特性的預設值時顯示的使用者介面。 如果您要發行當地語系化的應用程式，您必須指定的語言和文化特性，以符合當地語系化的版本。 這取決於`Publish language`專案的屬性。  
  
 `Publish language`屬性可以設定**發行選項**對話方塊中，從存取**發行**頁面**專案設計工具**。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-change-the-publish-language"></a>若要變更發行語言  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**選項** 按鈕以開啟**發行選項** 對話方塊。  
  
4.  按一下**描述**。  
  
5.  中**發行選項**對話方塊方塊中，選取語言和文化特性從**發行語言**下拉式清單，然後按一下**確定**。  
  
## <a name="see-also"></a>請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)