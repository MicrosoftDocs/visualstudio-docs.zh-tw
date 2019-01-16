---
title: HOW TO：自訂 ClickOnce 應用程式的預設網頁 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97ab1335b846ecccf31addfa134fc63396dc841b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861273"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>HOW TO：自訂 ClickOnce 應用程式的預設網頁
發行 ClickOnce 應用程式到 Web，當網頁自動產生及發行以及應用程式。 預設的網頁包含應用程式和安裝應用程式、 安裝必要元件，或存取 MSDN 上的說明連結的名稱。  
  
> [!NOTE]
>  您在頁面看到的實際連結相依於檢視頁面所在的電腦，以及您要納入的必要條件。  
  
 網頁的預設名稱是*Publish.htm*; 您可以變更中的名稱**專案設計工具**。 如需詳細資訊，請參閱[＜How to：指定 ClickOnce 應用程式的發佈頁面](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)。  
  
 *Publish.htm*偵測到較新版本時，才發佈網頁。  
  
> [!NOTE]
>  您對所做變更您**發佈**設定不會影響*Publish.htm*頁面上，有一個例外狀況： 如果您新增或移除最初發行之後的必要元件，必要條件清單將會已經不正確。 您必須編輯必要條件的連結，以反映所做的變更的文字。  
  
### <a name="to-customize-the-publish-web-page"></a>若要自訂 [發行 Web] 頁面  
  
1.  發行 ClickOnce 應用程式到 Web 的位置。 如需詳細資訊，請參閱[＜How to：使用 [發佈精靈] 發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
2.  在 Web 伺服器上，開啟*Publish.htm* Visual Web 設計工具或另一個 HTML 編輯器中的檔案。  
  
3.  自訂所需的頁面，並將它儲存。  
  
4.  選擇性。 若要防止 Visual Studio 覆寫您自訂的發行的網頁，請取消選取**自動產生部署網頁之後, 每個發行**中**發行選項** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：隨著 ClickOnce 應用程式安裝必要軟體](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [如何：指定 ClickOnce 應用程式的發佈頁面](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)