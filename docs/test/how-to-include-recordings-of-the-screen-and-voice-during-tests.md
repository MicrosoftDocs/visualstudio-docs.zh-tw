---
title: 在測試期間錄製螢幕及聲音
description: 瞭解如何設定診斷資料介面卡，以在 Visual Studio 中記錄執行測試之使用者的螢幕和聲音。
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08ae6d19327a956b5dab71fa30b0b33742390d2b
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440983"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>如何：使用測試設定在測試期間包含螢幕和聲音錄製

您可以在 Visual Studio 的組態編輯器中設定診斷資料配接器，用於錄製執行測試之使用者的螢幕和聲音。 這個診斷資料配接器會儲存測試期間錄製的桌面工作階段螢幕和聲音。 錄製會和測試結果一起儲存，也可以附加至 Bug。 其他小組成員可以使用這段錄製內容找出難以重現的應用程式缺陷。

> [!WARNING]
> 螢幕和聲音錄製不支援多重監視器組態。

螢幕和聲音錄製器可以搭配手動或自動化測試使用。 例如，如果遠端執行自動程式碼 UI 測試，您可能想要錄製桌面來查看自動程式碼 UI 測試執行時的情況。 如需如何從遠端擷取螢幕和聲音錄製的詳細資訊，請參閱[如何：將您的測試代理程式設定為執行與桌面互動的測試](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>若要設定測試設定的螢幕和聲音錄製

1. 開啟您要設定錄製螢幕和聲音的測試設定。 如需詳細資訊，請參閱[在測試時收集診斷資料 (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true) 或[使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)。

2. 在測試設定中，選取要用來錄製螢幕和聲音的 [角色]。

    > [!NOTE]
    > 若為手動測試和自動化測試，該項是執行測試的機器。

3. 選取 [螢幕和聲音錄製器]，然後選擇 [設定]。

     [設定診斷資料配接器 - 螢幕和聲音錄製器] 對話方塊隨即顯示。

     ![視訊組態](../test/media/testsettingvideoconfiggdr.png)

4. (選擇性) 選取 [啟用錄音] 擷取錄製中的音訊內容。

5. (選擇性) 若要指定針對失敗和成功的測試儲存螢幕和聲音錄製，請選取 [如果測試案例成功即儲存錄製] 旁的核取方塊。

    > [!WARNING]
    > 如果您選取 [如果測試案例成功即儲存錄製]，錄製內容會與測試結果一併儲存，並且使用伺服器上的儲存空間。 您可以使用 **Test Attachment Cleaner** 工具清除這些附件。

6. 在 [螢幕錄製品質] 底下，設定下列下拉式清單選項：

    1. **畫面播放速率：** 指定您要在螢幕和聲音錄製中使用的每秒畫面格數。 預設值為每秒 4 個畫面格。 您可以指定介於 2 和 20 之間的值。

    2. **位元速率：** 指定要在螢幕和聲音錄製中使用的每秒 KB 數。 預設值為 512。 您可以指定介於 512 和 10,000 之間的值。

    3. **品質(1-100)：** 您可以指定範圍介於 1 和 100 之間的螢幕和聲音錄製品質。 預設值為 50 (中間範圍)。

7. 選擇 [確定]。 針對測試設定，現在已經設定和儲存診斷追蹤收集器設定。

    ::: moniker range="vs-2017"
    > [!TIP]
    > 若要重設此診斷資料配接器的組態，請在 Visual Studio 中選擇 [重設為預設組態]，在 Microsoft Test Manager 中則選擇 [重設為預設值]。
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!TIP]
    > 若要重設此診斷資料介面卡的設定，請選擇 [Visual Studio 中的 [ **重設為預設設定** ]。
    ::: moniker-end

## <a name="see-also"></a>另請參閱

- [在測試時收集診斷資料 (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [在手動測試中收集診斷資料 (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)
- [執行手動測試 (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)