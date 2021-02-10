---
title: 指定技術支援的連結 |Microsoft Docs
description: 深入瞭解發行 ClickOnce 應用程式的 [支援 URL] 屬性，其可識別使用者取得資訊的網頁或檔案共用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Support URL property
- product support, specifying URL for ClickOnce applications
- Web pages, ClickOnce
- Web sites, creating for ClickOnce support
- ClickOnce deployment, specifying support Web page address
- customer support, ClickOnce applications
- URLs, ClickOnce applications
ms.assetid: 500aebee-545e-4831-a78b-b8671a008015
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 335f41abf0ca2914ca603f7adbce7dea98eee028
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940484"
---
# <a name="how-to-specify-a-link-for-technical-support"></a>How to: Specify a link for Technical Support (如何：指定技術支援的連結)
發佈 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，[ **支援 URL** ] 屬性會識別網頁或檔案共用，讓使用者可以前往該頁面取得應用程式的相關資訊。 這個屬性是選擇性的;如果有提供，URL 將會顯示在應用程式的 [ **新增或移除程式** ] 對話方塊中。

 [**支援 URL** ] 屬性可以在 [**專案設計** 工具] 的 [**發行**] 頁面上設定。

### <a name="to-specify-a-support-url"></a>若要指定支援 URL

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [Publish (發行)]  索引標籤。

3. 按一下 [ **選項** ] 按鈕，開啟 [ **發行選項** ] 對話方塊。

4. 按一下 [ **描述**]。

5. 在 [ **支援 URL** ] 欄位中，輸入網站、網頁或 UNC 共用的完整路徑。

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)