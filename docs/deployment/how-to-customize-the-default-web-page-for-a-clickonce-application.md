---
title: 自訂 ClickOnce 應用程式的預設網頁
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ee4c1211840f17afe371961dea644372cd63efb
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382467"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>如何：自訂 ClickOnce 應用程式的預設 Web 頁面
將 ClickOnce 應用程式發行至 Web 時，會自動產生一個網頁，並與應用程式一起發行。 預設頁面會包含應用程式的名稱，以及在 MSDN 上安裝應用程式、安裝必要條件或存取說明的連結。

> [!NOTE]
> 您在頁面上看到的實際連結取決於正在查看頁面的電腦，以及您所包含的必要條件。

 網頁的預設名稱為*Publish.htm*;您可以在 [**專案設計**工具] 中變更名稱。 如需詳細資訊，請參閱[如何：指定 ClickOnce 應用程式的發行頁面](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)。

 只有在偵測到較新的版本時，才會發佈*Publish.htm*的網頁。

> [!NOTE]
> 您對**發行**設定所做的變更不會影響*Publish.htm*頁面，但有一個例外：如果您在最初發佈之後加入或移除必要條件，必要條件清單將不再正確。 您將需要編輯必要條件連結的文字，以反映變更。

### <a name="to-customize-the-publish-web-page"></a>若要自訂發行網頁

1. 將 ClickOnce 應用程式發行至 Web 位置。 如需詳細資訊，請參閱[如何：使用發行嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。

2. 在 Web 服務器上，于 Visual Web Designer 或其他 HTML 編輯器中開啟*Publish.htm*檔案。

3. 視需要自訂頁面並加以儲存。

4. 選擇性。 若要防止 Visual Studio 覆寫自訂的發行網頁，請取消核取 [**發行選項**] 對話方塊中的 [**每次發行之後自動產生部署網頁**]。

## <a name="see-also"></a>另請參閱
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [How to: Install prerequisites with a ClickOnce application](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) (如何：使用 ClickOnce 應用程式安裝必要元件)
- [如何：指定 ClickOnce 應用程式的發行頁面](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)