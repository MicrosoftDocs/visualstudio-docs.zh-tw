---
title: HOW TO：停用 ClickOnce 應用程式的 URL 啟動 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6841b8a91cec24f467f6e3f684cbb27e25c9fa63
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045612"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>HOW TO：停用 ClickOnce 應用程式的 URL 啟動

一般而言，從 Web 伺服器安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式後，其將立即自動啟動。 基於安全性理由，您可以決定停用此行為，並告知使用者改從 [開始] 功能表啟動應用程式。 下列程序描述如何停用 URL 啟用。

這項技術僅適用於安裝在使用者電腦上的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，其來自 Web 伺服器。 此技術不得用於僅限線上使用的應用程式，其只能使用 URL 啟動。 如需僅限線上使用及已安裝應用程式之間差異的詳細資訊，請參閱[選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。

此程序會使用 Windows 軟體開發套件 (SDK) 工具 MageUI.exe。 如需有關這項工具的詳細資訊，請參閱 < [MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)。 您也可以執行使用 Visual Studio 這個程序。

## <a name="procedure"></a>程序

### <a name="to-disable-url-activation-for-your-application"></a>若要停用應用程式的 URL 啟用

1. 開啟 MageUI.exe 中的部署資訊清單。 如果您尚未建立一個，請依照下列中的步驟[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。

2. 選取 [部署選項] 索引標籤。

3. 清除 [安裝後自動執行應用程式] 核取方塊。

4. 儲存並簽署該資訊清單。

## <a name="see-also"></a>另請參閱

- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)