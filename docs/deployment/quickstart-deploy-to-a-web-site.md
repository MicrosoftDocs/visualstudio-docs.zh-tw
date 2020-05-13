---
title: 發行至網站
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1236c3057cd209bd5c7c81304a2168704927c506
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "71127940"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>使用 Visual Studio 將 Web 應用程式發行至網站

æ‚¨å¯ä»¥ä½¿ç”¨ [ç™¼è¡Œ]**** å·¥å…·ï¼Œå¾ž Visual Studio å°‡ ASP.NETã€ASP.NET Coreã€.NET Core åŠ Python æ‡‰ç”¨ç¨‹å¼ç™¼è¡Œè‡³ç¶²ç«™ã€‚ é‡å° Node.jsï¼Œæ”¯æ´é€™äº›æ­¥é©Ÿä½†ä½¿ç”¨è€…ä»‹é¢ä¸åŒã€‚

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> å¦‚æžœæ‚¨éœ€è¦å°‡ Windows æ¡Œé¢æ‡‰ç”¨ç¨‹å¼ç™¼è¡Œè‡³ç¶²è·¯æª”æ¡ˆå…±ç”¨ï¼Œè«‹åƒé–±[ä½¿ç”¨ ClickOnce éƒ¨ç½²æ¡Œé¢æ‡‰ç”¨ç¨‹å¼](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# æˆ– Visual Basic)ã€‚ æœ‰é—œC++/CLIï¼Œè«‹åƒé–±[ä½¿ç”¨ ClickOnce éƒ¨ç½²æœ¬æ©Ÿæ‡‰ç”¨](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)ï¼Œæˆ–è€…å°æ–¼ C/C++ï¼Œè«‹åƒé–±[ä½¿ç”¨å®‰è£ç¨‹å¼éƒ¨ç½²æœ¬æ©Ÿæ‡‰ç”¨](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)ã€‚

## <a name="publish-to-a-web-site"></a>發行至網站

1. åœ¨ [æ–¹æ¡ˆç¸½ç®¡] ä¸­ï¼Œä»¥æ»‘é¼ å³éµæŒ‰ä¸€ä¸‹å°ˆæ¡ˆï¼Œç„¶å¾Œé¸æ“‡ [ç™¼è¡Œ]**** (æˆ–ä½¿ç”¨ [å»ºç½®]**** > [ç™¼è¡Œ]**** åŠŸèƒ½è¡¨é …ç›®)ã€‚

    ![è§£æ±ºæ–¹æ¡ˆè³‡æºç®¡ç†å™¨ä¸­å°ˆæ¡ˆå…§å®¹åŠŸèƒ½è¡¨ä¸Šçš„"ç™¼ä½ˆ"å‘½ä»¤](../deployment/media/quickstart-publish.png "é¸æ“‡ [ç™¼è¡Œ]")

1. å¦‚æžœæ‚¨ä¹‹å‰å·²è¨­å®šä»»ä½•ç™¼è¡Œè¨­å®šæª”ï¼Œ[ç™¼è¡Œ]**** çª—æ ¼æœƒéš¨å³å‡ºç¾ã€‚ é¸å– [å»ºç«‹æ–°è¨­å®šæª”]****ã€‚

1. åœ¨ [æŒ‘é¸ç™¼è¡Œç›®æ¨™]**** å°è©±æ–¹å¡Šä¸­ï¼Œé¸æ“‡ [IISã€FTP ç­‰ç­‰]****ã€‚

    ![é¸æ“‡ [IISã€FTP ç­‰ç­‰]ã€‚](../deployment/media/quickstart-publish-iis-ftp.png "é¸æ“‡ [IISã€FTP ç­‰ç­‰]ã€‚")

1. é¸å– [ç™¼è¡Œ]****ã€‚ è¨­å®šæª”ç™¼è¡Œè¨­å®šå°è©±æ–¹å¡Šéš¨å³é–‹å•Ÿã€‚

    ![選擇資料夾](../deployment/media/quickstart-publish-settings-web.png "選擇資料夾")

1. åœ¨ [ç™¼è¡Œæ–¹æ³•]**** æ¬„ä½ä¸­ï¼Œé¸æ“‡ä¸€ç¨®æ–¹æ³•ï¼Œä¾‹å¦‚ [Web Deploy]**** æˆ– [FTP]****ã€‚ æ‚¨çœ‹åˆ°ä¹‹è¨­å®šæŽ¥ä¸‹ä¾†æœƒå°æ‡‰è‡³æ‚¨çš„ç™¼è¡Œæ–¹æ³•ã€‚ Web Deploy å¯ç°¡åŒ–å°‡ Web æ‡‰ç”¨ç¨‹å¼å’Œç¶²ç«™éƒ¨ç½²åˆ° IIS ä¼ºæœå™¨çš„ä½œæ¥­ï¼Œè€Œä¸”å¿…é ˆå®‰è£ç‚ºä¼ºæœå™¨ä¸Šçš„æ‡‰ç”¨ç¨‹å¼ã€‚ è«‹ä½¿ç”¨ [Web platform installer](https://www.microsoft.com/web/downloads/platform.aspx) é€²è¡Œå®‰è£ã€‚

1. è¨­å®šç™¼è¡Œæ–¹æ³•çš„å¿…è¦è¨­å®šï¼Œç„¶å¾Œé¸å– [é©—è­‰é€£ç·š]****ã€‚ å¦‚æžœä¼ºæœå™¨æˆ–ç›®æ¨™å¯ä¾›ä½¿ç”¨ä¸”æ‚¨çš„è¨­å®šæ­£ç¢ºï¼Œå‰‡æœƒé¡¯ç¤ºä¸€å‰‡è¨Šæ¯æŒ‡å‡ºå·²é©—è­‰é€£ç·šï¼Œä¸”æ‚¨å·²ç¶“æº–å‚™å¥½ç™¼è¡Œã€‚

    ![é©—è­‰æ‚¨çš„é€£æŽ¥](../deployment/media/quickstart-publish-web-deploy.png "é©—è­‰æ‚¨çš„é€£æŽ¥")

1. é¸å– [è¨­å®š]**** è¨­å®šå…¶ä»–éƒ¨ç½²è¨­å®šï¼Œä¾‹å¦‚æ˜¯å¦è¦éƒ¨ç½² [åµéŒ¯] æˆ– [ç™¼è¡Œ] çµ„æ…‹ï¼Œç„¶å¾Œé¸å– [å„²å­˜]****ã€‚ å¦‚æžœæ‚¨è¦é ç«¯åµéŒ¯ï¼Œå‰‡éœ€è¦ [åµéŒ¯] çµ„æ…‹ã€‚

1. è‹¥è¦ç™¼è¡Œï¼Œè«‹é¸å– [ç™¼è¡Œ]****ã€‚ [è¼¸å‡º] è¦–çª—æœƒé¡¯ç¤ºéƒ¨ç½²é€²åº¦å’Œçµæžœã€‚

## <a name="next-steps"></a>後續步驟

在本快速入門中，您已了解如何使用 Visual Studio 建立發行設定檔。 您也可以匯入發行設定來設定發行設定檔。

> [!div class="nextstepaction"]
> [匯入發佈設定並部署至 IIS](tutorial-import-publish-settings-iis.md)
