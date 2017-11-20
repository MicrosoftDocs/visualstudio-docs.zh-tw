---
title: "如何： 自訂 ClickOnce 應用程式的預設 Web 網頁 |Microsoft 文件"
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
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: "14"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: fefafa0f9ea04a62d6ae79bd18834e36a1480f29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>如何：自訂 ClickOnce 應用程式的預設 Web 網頁
當發行 ClickOnce 應用程式 web，網頁上自動產生及發行以及應用程式。 預設頁面包含的應用程式和安裝應用程式、 安裝必要元件，或存取 MSDN 上的說明連結的名稱。  
  
> [!NOTE]
>  您在頁面看到的實際連結取決於檢視的網頁位置的電腦和所包含的必要條件。  
  
 網頁上的預設名稱是 Publish.htm;您可以變更在名稱**專案設計工具**。 如需詳細資訊，請參閱[How to： 指定 ClickOnce 應用程式的發行頁](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)。  
  
 Publish.htm Web 網頁會在偵測到較新版本時，才發行。  
  
> [!NOTE]
>  您對所做變更您**發行**設定不會影響 Publish.htm 頁面上，有一個例外狀況： 如果您新增或移除必要條件最初發行之後的必要條件清單已經不正確。 您必須編輯以反映變更必要條件連結文字。  
  
### <a name="to-customize-the-publish-web-page"></a>若要自訂發行網頁  
  
1.  發行 ClickOnce 應用程式到 Web 位置。 如需詳細資訊，請參閱[如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
2.  在 Web 伺服器上，開啟 Publish.htm 檔案在 Visual Web 設計工具或其他 HTML 編輯器中。  
  
3.  自訂所需的頁面，並將其儲存。  
  
4.  選擇項。 若要防止 Visual Studio 無法覆寫自訂的發行網頁，取消核取**自動產生部署網頁之後, 每個發行**發行選項 對話方塊中。  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何： 使用 ClickOnce 應用程式安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [如何：指定 ClickOnce 應用程式的發行頁面](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)