---
title: 啟用 CD 安裝的 AutoStart |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28fa4830c3ea5ff840e0d58f6d31f718c28ec3fb
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90850939"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>How to: Enable AutoStart for CD installations (如何：啟用 CD 安裝的 AutoStart)
藉由卸載 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 式媒體（例如 cd-rom 或 dvd-rom）部署應用程式時，您可以啟用， `AutoStart` 讓 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式在插入媒體時自動啟動。

 `AutoStart`可以在 [**專案設計**工具] 的 [**發行**] 頁面上啟用。

### <a name="to-enable-autostart"></a>啟用自動啟動

1. 在 **方案總管**中選取專案時，在 [ **專案** ] 功能表上按一下 [ **屬性**]。

2. 按一下 [Publish (發行)] **** 索引標籤。

3. 按一下 [ **選項** ] 按鈕。

     [ **發行選項** ] 對話方塊隨即出現。

4. 按一下 [部署]****。

5. 選取 [若 **要安裝 cd，請在插入光碟時自動啟動安裝** ] 核取方塊。

     發行應用程式時，會將 *自動完成 .inf* 檔案複製到發行位置。

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)