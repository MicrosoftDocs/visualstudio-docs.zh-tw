---
title: 如何： 指定 ClickOnce 離線或線上安裝模式 |Microsoft Docs
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
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 7f277966070e142ebc24d70acfcf4bf5502f419a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489816"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>如何：指定 ClickOnce 離線或線上安裝模式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 指定 ClickOnce 離線或線上安裝模式](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-the-clickonce-offline-or-online-install-mode)。  
  
`Install Mode`針對[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式可讓您判斷應用程式是在離線或線上時使用。 當您選擇**應用程式只提供線上**，使用者必須能夠存取[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]發行 （網頁或檔案共用） 才能執行應用程式的位置。 當您選擇**應用程式也可以在離線時**，應用程式會將項目加入**開始**功能表並**新增或移除程式** 對話方塊中，使用者是無法在未連線時，執行應用程式。  
  
 `Install Mode`上，可以設定**發佈**頁面**專案設計工具**。  
  
 **附註**`Install Mode`也可以設定使用發佈精靈。 如需詳細資訊，請參閱 <<c0> [ 如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>將 ClickOnce 應用程式提供線上只  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [**發佈**] 索引標籤。  
  
3.  在 **安裝模式和設定**區域中，按一下**應用程式只提供線上**選項按鈕。  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>若要使用 ClickOnce 應用程式線上或離線  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [**發佈**] 索引標籤。  
  
3.  在 **安裝模式和設定**區域中，按一下**應用程式也可以在離線時**選項按鈕。  
  
     應用程式安裝時，將項目加入**開始** 功能表並**新增或移除程式**控制項台中。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)



