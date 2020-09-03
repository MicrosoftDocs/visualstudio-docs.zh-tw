---
title: 如何：指定 ClickOnce 應用程式的發行頁面 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63356c6eb423ddead54290cc11c865a5102f55f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202170"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>如何：指定 ClickOnce 應用程式的發行頁面
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

發行 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式時，會產生預設的網頁 ( # A0) ，並隨應用程式一起發行。 此頁面包含應用程式的名稱、用來安裝應用程式的連結和（或）任何必要條件，以及描述的說明主題連結 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 。 專案的 [ **發行] 頁面** 屬性可讓您為應用程式指定網頁的名稱 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 。  
  
 一旦指定發佈頁面之後，下次發佈時，它就會複製到發佈位置;如果您再次發佈，將不會覆寫此檔案。 如果您想要自訂頁面的外觀，您可以這麼做，而不必擔心會遺失您的變更。 如需詳細資訊，請參閱 [如何：自訂 ClickOnce 預設網頁](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)。  
  
 [**發行] 頁面**屬性可以在 [**發行選項**] 對話方塊中設定，可從 [**專案設計**工具] 的 [**發行**] 窗格存取。  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>若要指定 ClickOnce 應用程式的自訂網頁  
  
1. 在 **方案總管**中選取專案時，在 [ **專案** ] 功能表上按一下 [ **屬性**]。  
  
2. 選取 [ **發行** ] 窗格。  
  
3. 按一下 [ **選項** ] 按鈕，開啟 [ **發行選項** ] 對話方塊。  
  
4. 按一下 [部署]****。  
  
5. 在 [ **發行選項** ] 對話方塊中，確定已選取 [ **發行後開啟部署網頁** ] 核取方塊 (預設為選取) 。  
  
6. 在 [ **部署 web 頁面：** ] 方塊中，輸入網頁的名稱，然後按一下 **[確定]**。  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>防止發佈頁面在您每次發佈時啟動  
  
1. 在 **方案總管**中選取專案時，在 [ **專案** ] 功能表上按一下 [ **屬性**]。  
  
2. 選取 [ **發行** ] 窗格。  
  
3. 按一下 [ **選項** ] 按鈕，開啟 [ **發行選項** ] 對話方塊。  
  
4. 按一下 [部署]****。  
  
5. 在 [ **發行選項** ] 對話方塊中，清除 [ **發行後開啟部署網頁** ] 核取方塊。  
  
## <a name="see-also"></a>另請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發佈嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [如何：自訂 ClickOnce 預設網頁](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)
