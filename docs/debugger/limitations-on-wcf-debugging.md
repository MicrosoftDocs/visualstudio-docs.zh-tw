---
title: WCF 偵錯的限制 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e1733539c3f2da5d961a347e2f1c818d83257d2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721481"
---
# <a name="limitations-on-wcf-debugging"></a>WCF 偵錯的限制
您可以使用三種方式開始對 WCF 服務進行偵錯：

- 您要對呼叫服務的用戶端處理序進行偵錯。 偵錯工具會逐步執行服務。 服務不需要與用戶端應用程式位於相同的方案內。

- 您要對要求服務的用戶端處理序進行偵錯。 服務必須是方案的一部分。

- 使用 [附加至處理序] 即可附加至目前正在執行的服務。 偵錯會從服務內部開始進行。

  本主題將描述這些情節的限制。

## <a name="limitations-on-stepping-into-a-service"></a>逐步執行服務的限制
 若要從您要進行偵錯的用戶端應用程式逐步執行服務，則必須符合下列條件：

-   用戶端必須使用同步用戶端物件呼叫服務。

-   協定作業不可以是單向的。

-   如果伺服器非同步，您就無法在服務內部執行程式碼時檢視完整的呼叫堆疊。

-   您必須在 app.config 或 Web.config 檔案中使用下列程式碼啟用偵錯：

    ```xml
    <system.web>
      <compilation debug="true" />
    </system.web>
    ```

     這個程式碼只需要加入一次。 您可以藉由編輯 .config 檔案新增這個程式碼，或使用 [附加至處理序] 將這個程式碼附加至服務。 您在服務上使用 [附加至處理序] 時，偵錯程式碼就會自動新增至 .config 檔案。 完成這個動作後，您就可以進行偵錯及逐步執行服務，而不需要編輯 .config 檔案。

## <a name="limitations-on-stepping-out-of-a-service"></a>跳離服務的限制
 跳離服務並返回用戶端的限制，與逐步執行服務所述的限制相同。 此外，您必須將偵錯工具附加至用戶端。 如果您要對用戶端進行偵錯並逐步執行服務，則偵錯工具會保持附加至服務的狀態。 不論您是使用 [開始偵錯] 啟動用戶端，或是使用 [附加至處理序] 附加至用戶端，都是如此。 如果您藉由附加至服務的方式開始進行偵錯，則偵錯工具尚未附加至用戶端。 在這種情況下，如果您必須跳離服務並返回用戶端，則必須先使用 [附加至處理序] 手動附加至用戶端。

## <a name="limitations-on-automatic-attach-to-a-service"></a>自動附加至服務的限制
 自動附加至服務具有下列限制：

- 服務必須是您要偵錯之 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案的一部分。

- 服務必須已裝載。 服務可以是網站專案 (檔案系統和 HTTP)、Web 應用程式專案 (檔案系統和 HTTP)，或 WCF 服務庫專案的一部分。 WCF 服務庫專案可以是服務庫或工作流程服務庫。

- 服務必須從 WCF 用戶端叫用。

- 您必須在 app.config 或 Web.config 檔案中使用下列程式碼啟用偵錯：

  ```xml
  <system.web>
    <compilation debug="true" />
  <system.web>
  ```

## <a name="self-hosting"></a>自我裝載
 「自我裝載服務」是一項不會在 IIS、WCF 服務主機或 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 程式開發伺服器內部執行的 WCF 服務。 如需如何偵錯自我裝載的服務的資訊，請參閱[如何： 偵錯自我裝載 WCF 服務](../debugger/how-to-debug-a-self-hosted-wcf-service.md)。

## <a name="self-hosting"></a>自我裝載
 若要啟用 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 或 3.5 應用程式的偵錯功能，則必須先安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 或 3.5，再安裝 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]。 如果先安裝 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 再安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 或 3.5，當您嘗試對 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 或 3.5 應用程式進行偵錯時，就會發生錯誤。 錯誤訊息為「無法自動逐步執行伺服器」。 若要修正此問題，請使用 Windows**控制台中** > **程式和功能**修復您[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]安裝。

## <a name="see-also"></a>請參閱
- [偵錯 WCF 服務](../debugger/debugging-wcf-services.md)
- [如何：偵錯自我裝載的 WCF 服務](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
