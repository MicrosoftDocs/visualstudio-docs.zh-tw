---
title: 如何： 變更 ClickOnce 應用程式發行語言 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 90699b4e12c8384327a3840799506e393bed2e82
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497602"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>如何：變更 ClickOnce 應用程式的發行語言
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[How to: Change the Publish Language for a ClickOnce Application](https://docs.microsoft.com/visualstudio/deployment/how-to-change-the-publish-language-for-a-clickonce-application)。  
  
發佈時[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式，在安裝語言與您的開發電腦的文化特性的預設值時顯示的使用者介面。 如果您要發行當地語系化的應用程式，您必須指定語言和文化特性，以符合當地語系化的版本。 這取決於`Publish language`專案的屬性。  
  
 `Publish language`屬性可以在中設定**發行選項**對話方塊中，從可存取**發行**頁面**專案設計工具**。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-change-the-publish-language"></a>若要變更的發行語言  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [**發佈**] 索引標籤。  
  
3.  按一下 **選項** 按鈕以開啟**發行選項** 對話方塊。  
  
4.  按一下 **描述**。  
  
5.  在 **發行選項**對話方塊方塊、 選取語言和文化特性，從**發行語言**下拉式清單中，然後再按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



