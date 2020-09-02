---
title: 如何：指定 ClickOnce 離線或線上安裝模式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: d4111ca5aee4a405a4a797dbfee14a3d4b50435f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149745"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>如何：指定 ClickOnce 離線或線上安裝模式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Install Mode` [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式會決定應用程式是否可離線或在線上使用。 當您選擇 **[應用程式只能在線上使用**] 時，使用者必須能夠存取 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 發佈位置 (網頁或檔案共用) ，才能執行應用程式。 當您選擇 **應用程式**時，應用程式也會在 [ **開始** ] 功能表和 [ **新增或移除程式** ] 對話方塊中加入專案。當應用程式未連線時，使用者可以執行該應用程式。  
  
 `Install Mode`可以在 [**專案設計**工具] 的 [**發行**] 頁面上設定。  
  
 **注意**`Install Mode`也可以使用 [發佈嚮導] 來設定。 如需詳細資訊，請參閱 [如何：使用發佈嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>使 ClickOnce 應用程式只能在線上使用  
  
1. 在方案總管 **** 中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。  
  
2. 按一下 [Publish (發行)] **** 索引標籤。  
  
3. 在 [ **安裝模式和設定]** 區域中，按一下 [ **應用程式只能在線上使用** ] 選項按鈕。  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>使 ClickOnce 應用程式可在線上或離線使用  
  
1. 在方案總管 **** 中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。  
  
2. 按一下 [Publish (發行)] **** 索引標籤。  
  
3. 在 [ **安裝模式和設定]** 區域中，按一下 [ **應用程式也可離線使用** ] 選項按鈕。  
  
     安裝時，應用程式會在 [ **開始** ] 功能表中加入專案，並在主控台中 **新增或移除程式** 。  
  
## <a name="see-also"></a>另請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發佈嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)
