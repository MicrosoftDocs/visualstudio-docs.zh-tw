---
title: Self-Hosted WCF 服務的 Debug |Microsoft 檔
description: 瞭解如何對自我裝載的 WCF 服務進行調試。  (但不一定能) 的最簡單方式，就是將 Visual Studio 設定為同時啟動用戶端和伺服器。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3cd11966347cd90576eb78a59f6c7eb96cc697ef
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155077"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>如何：偵錯自我裝載的 WCF 服務
「自我裝載服務」是一項不會在 IIS、WCF 服務主機或 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 程式開發伺服器內部執行的 WCF 服務。 若要將自我裝載的 WCF 錯用，最簡單的方式是將設定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 為在您選擇 [**調試** 程式] 功能表上的 [**開始調試** 程式] 時同時啟動用戶端和伺服器。

 如果 WCF 服務是自我裝載，或無法以這種方式啟動的進程（例如 NT 服務），您就無法使用這個方法。 相反地，您可以執行下列其中一項：

- 手動將偵錯工具附加至裝載進程。 如需詳細資訊，請參閱 [附加至正在](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)執行的進程。

     — 或者—

- 開始對用戶端進行調試，然後逐步執行對服務的呼叫。 這需要您在 app.config 檔案中啟用偵錯工具。 如需詳細資訊，請瞭解 [WCF 調試](../debugger/limitations-on-wcf-debugging.md)程式的限制。

### <a name="to-start-both-client-and-host-from-visual-studio"></a>若要從 Visual Studio 啟動用戶端和主機

1. 建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 包含用戶端和伺服器專案的方案。

2. 當您在 [**調試** 程式] 功能表上選擇 [**啟動**] 時，請將方案設定為啟動用戶端和伺服器進程。

   1. 在 [ **方案 Explorer**] 中，以滑鼠右鍵按一下方案名稱。

   2. 按一下 [ **設定啟始專案**]。

   3. 在 [ **方案 \<name> 屬性** ] 對話方塊中，選取 [ **多個啟始專案**]。

   4. 在 [ **多個啟始專案** ] 方格中，于對應到伺服器專案的行上按一下 [ **動作** ]，然後選擇 [ **啟動**]。

   5. 在對應至用戶端專案的行上，按一下 [ **動作** ]，然後選擇 [ **啟動**]。

   6. 按一下 [確定]  。

## <a name="see-also"></a>另請參閱
- [偵錯 WCF 服務](../debugger/debugging-wcf-services.md)
- [WCF 調試的限制](../debugger/limitations-on-wcf-debugging.md)
- [如何：逐步執行 WCF 服務](../debugger/how-to-step-into-wcf-services.md)
