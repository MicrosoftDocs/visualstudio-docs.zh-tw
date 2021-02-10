---
title: 將內容參數新增至負載測試回合設定
description: 瞭解如何使用負載測試編輯器（可讓您參數化字串），建立要在負載測試回合設定中使用的內容參數。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 732f8e0cb88443533f74e843dde04ec977f24ebd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942330"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>如何：將內容參數新增至負載測試回合設定

使用 **新的負載測試精靈** 建立負載測試之後，您可以使用 **負載測試編輯器** 來變更情節屬性，以符合您的測試需求和目標。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> 如需回合設定屬性及其描述的完整清單，請參閱[負載測試回合設定屬性](../test/load-test-run-settings-properties.md)。

您可以使用 [負載測試編輯器]，建立可用於負載測試回合設定的內容參數。 內容參數可讓您參數化字串。

假設您的負載測試包含的 Web 效能測試已透過內容參數使用參數化的 Web 伺服器 URL。 您就可以將內容參數加入至使用的名稱值與 Web 效能測試中所使用之名稱值相同的負載測試回合設定。 這樣當您執行負載測試時，就會將 Web 效能測試對應至不同的伺服器。 例如，如果您的負載測試包含的 Web 效能測試，是使用名為 WebServer1 的內容參數做為 URL 中 Web 伺服器的名稱。 那麼如果您在負載測試回合設定中指定同樣名為 WebServer1 的內容參數，則負載測試將會使用您在負載測試回合設定中指派的內容參數。 為了加以區別，如果負載測試中的 Web 效能測試使用的內容參數名稱與負載測試的內容參數相同，負載測試的內容參數將會覆寫 Web 效能測試的內容參數。

> [!WARNING]
> 當您在回合設定中使用內容參數時，務必小心不要覆寫 Web 效能測試的內容參數。 請避免使用相同的內容參數名稱，除非您是刻意這樣做。

如果您將 Webserver1 內容參數的值指派給 `http://CorporateStagingWebServer`，就可以在整個負載測試期間使用 `WebServer1`，因而能夠輕鬆地隨時將值變更為不同的網頁伺服器。

此外，藉由在不同的負載測試回合設定中使用相同名稱將不同的值指派給內容參數，就能使用不同的環境執行負載測試：

- 企業臨時網頁伺服器回合設定：名為 `WebServer1=http://CorporateStagingWebServer` 的內容參數

- 企業實際執行網頁伺服器回合設定：名為 `WebServer1=http://CorporateProductionWebServer` 的內容參數

  **從命令列變更回合設定**

  如果您想要從命令列使用不同的回合設定來運用內容參數策略，請使用下列命令：

  **Set Test.UseRunSetting= CorporateStagingWebServer**

  -和-

  **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>將內容參數加入至回合設定

1. 開啟負載測試。

2. 在 [負載測試編輯器] 的負載測試樹狀目錄中，展開 [回合設定] 資料夾。

3. 以滑鼠右鍵按一下要新增內容參數的特定回合設定，然後選擇 [新增內容參數]。

     新的內容參數隨即新增至負載測試樹狀目錄之 [回合設定] 資料夾內的 [內容參數] 資料夾。

     -或-

     如果回合設定已包含 [內容參數] 資料夾，您可以在該資料夾上按一下滑鼠右鍵，然後選擇 [新增內容參數]。

4. 在 [屬性] 視窗中，將 [名稱] 變更為適當的值 (例如 WebServer1)。 在 [ **屬性** ] 視窗中，將 **值** 變更為您要使用的參數 (例如 `http://CorporateStagingWebServer`) 。

5.  (選擇性) 重複步驟3到5，並針對 [ **值** ] 屬性使用不同的字串 (例如 `http://CorporateProductionWebServer`) 。

6. 選擇要成為使用中的回合設定。 在回合設定上開啟捷徑功能表，然後選擇 [設定為使用中]。

## <a name="see-also"></a>另請參閱

- [設定負載測試回合設定](../test/configure-load-test-run-settings.md)
