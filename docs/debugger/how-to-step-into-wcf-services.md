---
title: 逐步執行 WCF 服務 |Microsoft Docs
description: 逐步執行 Windows Communication Foundation (WCF) 服務。 如果它位於與用戶端相同的 Visual Studio 方案中，請在 WCF 服務內叫用中斷點。
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
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5f3a884698586cdd9a89ff62a090f02af3953a91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896636"
---
# <a name="how-to-step-into-wcf-services"></a>如何：逐步執行 WCF 服務
在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中，您可以逐步執行 WCF 服務。 如果 WCF 服務與用戶端都位於相同的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案，您就可以執行到達 WCF 服務內部的中斷點。

 您必須在 app.config 或 Web.config 檔案內啟用偵錯，才能使用逐步執行。 如需有關如何啟用偵錯工具以及逐步執行 WCF 服務之限制的詳細資訊，請參閱 [Wcf 調試](../debugger/limitations-on-wcf-debugging.md)程式的限制。

### <a name="to-step-into-a-wcf-service"></a>若要逐步執行 WCF 服務

1. 建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案，其中包含 WCF 用戶端和 WCF 服務專案。

2. 在 [方案總管] 中，以滑鼠右鍵按一下 WCF 用戶端專案，然後按一下 [設定為啟始專案]。

3. 在 app.config 或 web.config 檔案內啟用偵錯。 如需詳細資訊，請參閱 [WCF 調試](../debugger/limitations-on-wcf-debugging.md)程式的限制。

4. 在用戶端專案中要開始逐步執行的位置設定中斷點。 這通常會是在 WCF 服務呼叫之前。

5. 執行至中斷點，然後開始逐步執行。 偵錯工具將自動逐步執行服務。

## <a name="see-also"></a>另請參閱
- [偵錯 WCF 服務](../debugger/debugging-wcf-services.md)
- [WCF 調試的限制](../debugger/limitations-on-wcf-debugging.md)
- [如何： Self-Hosted WCF 服務的調試](../debugger/how-to-debug-a-self-hosted-wcf-service.md)