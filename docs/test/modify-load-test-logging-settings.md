---
title: 負載測試記錄設定
description: 瞭解如何修改負載測試記錄設定來控制收集到的效能資料量，這可能會導致非常大的結果檔。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: db84e5be44d70934331d9e7d9c47e78bc669bedb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838291"
---
# <a name="modify-load-test-logging-settings"></a>修改負載測試記錄設定

已完成之負載測試的負載測試結果包含效能計數器樣本，以及記錄檔中定期從受測電腦收集而來的錯誤資訊。 您可以在負載測試回合進行期間收集大量效能計數器樣本。 收集的效能資料量會視回合的時間長度、取樣間隔、受測電腦數目，以及要收集的計數器數目而定。 若為大型負載測試，則收集的效能資料量可能很容易就達到數個 GB。因此，您可能考慮修改將資料儲存到記錄檔的頻率。 請參閱[測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

「測試控制器」會在測試執行時，將所有收集的負載測試樣本資料多工緩衝處理至資料庫記錄。 像是計時詳細資料和錯誤詳細資料這類額外資料會在測試完成時載入至資料庫。

|Task|相關主題|
|-|-----------------------|
|**負載測試失敗時儲存記錄：** 您可以指定是否要在每次負載測試失敗時都儲存一次測試記錄。|-   [如何：指定測試失敗是否會儲存至測試記錄](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**設定記錄檔的檔案大小上限：** 您可以編輯與測試控制器服務建立關聯的 XML 組態檔，指定要用於記錄檔的檔案大小上限。|修改 *QTCcontroller.exe.config* XML 組態檔中的 `<add key="LogSizeLimitInMegs" value="20"/>`。|

## <a name="see-also"></a>另請參閱

- [設定負載測試回合設定](../test/configure-load-test-run-settings.md)
