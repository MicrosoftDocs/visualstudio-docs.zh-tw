---
title: 如何-指定 ClickOnce 離線或線上安裝模式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcd9eeedfdd2a4661e3744da369a6fadc11039a3
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381752"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>How to: Specify the ClickOnce offline or online install mode (如何：指定 ClickOnce 離線或線上安裝模式)
`Install Mode` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的會決定應用程式是否可在離線或上線時使用。 當您選擇**只能在線上使用應用程式**時，使用者必須擁有 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 發佈位置（網頁或檔案共用）的存取權，才能執行應用程式。 當您選擇**應用程式也可以離線使用**時，應用程式會將專案新增至 [**開始**] 功能表和 [**新增或移除程式**] 對話方塊;使用者可以在未連接時執行應用程式。

`Install Mode`可以在 [**專案設計**工具] 的 [**發行**] 頁面上設定。

> [!NOTE]
> `Install Mode`也可以使用 [發行嚮導] 來設定。 如需詳細資訊，請參閱[如何：使用發行嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。

### <a name="to-make-a-clickonce-application-available-online-only"></a>使 ClickOnce 應用程式只能在線上使用

1. 在方案總管 **** 中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。

2. 按一下 [Publish (發行)] **** 索引標籤。

3. 在 [**安裝模式和設定]** 區域中，按一下 [**應用程式只能在線上使用**] 選項按鈕。

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>讓 ClickOnce 應用程式可在線上或離線時使用

1. 在方案總管 **** 中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。

2. 按一下 [Publish (發行)] **** 索引標籤。

3. 在 [**安裝模式和設定]** 區域中，按一下 [**應用程式也可以在離線時使用**] 選項按鈕。

     安裝後，應用程式會將專案新增至 [**開始**] 功能表，以及 [控制台] 中的 [**新增或移除程式**]。

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)