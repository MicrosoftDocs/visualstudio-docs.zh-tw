---
title: 自訂 ClickOnce 應用程式的預設網頁
description: 瞭解當您將 ClickOnce 應用程式發行至 Web 時所產生的網頁，其中包含應用程式的名稱和其他資訊。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0377bdc5fa38c814bb5cd6ff02d12dcec117266d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900789"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>如何：自訂 ClickOnce 應用程式的預設 Web 頁面
將 ClickOnce 應用程式發行至 Web 時，會自動產生一個網頁，並隨應用程式一起發行。 預設頁面包含應用程式的名稱，以及安裝應用程式的連結、安裝必要條件，或存取 MSDN 上的說明。

> [!NOTE]
> 您在頁面上看到的實際連結，取決於正在查看頁面的電腦，以及您要包含的必要條件。

 預設的網頁名稱是 *Publish.htm*;您可以在 [ **專案設計** 工具] 中變更名稱。 如需詳細資訊，請參閱 [如何：指定 ClickOnce 應用程式的發行頁面](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)。

 只有在偵測到較新版本時，才會發行 *Publish.htm* 的網頁。

> [!NOTE]
> 您對 **發佈** 設定所做的變更不會影響 *Publish.htm* 頁面，但有一個例外狀況：如果您在初次發行之後新增或移除必要條件，必要條件清單將不再正確。 您將需要編輯必要條件連結的文字，以反映變更。

### <a name="to-customize-the-publish-web-page"></a>自訂發行網頁

1. 將 ClickOnce 應用程式發佈到 Web 位置。 如需詳細資訊，請參閱 [如何：使用發佈嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。

2. 在 Web 服務器上，開啟 Visual Web Designer 或其他 HTML 編輯器中的 *Publish.htm* 檔案。

3. 視需要自訂頁面並加以儲存。

4. 選擇性。 若要防止 Visual Studio 覆寫您自訂的發行網頁，請在 [**發行選項**] 對話方塊中，取消核取 [在 **每次發行之後自動產生部署網頁**]。

## <a name="see-also"></a>另請參閱
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [How to: Install prerequisites with a ClickOnce application](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) (如何：使用 ClickOnce 應用程式安裝必要元件)
- [如何：指定 ClickOnce 應用程式的發行頁面](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)