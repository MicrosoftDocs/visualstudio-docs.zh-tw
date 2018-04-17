---
title: 從命令列設定 Visual Studio 負載測試回合設定 | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: e7a9a7dec6fffdb51cf71ff5a45a2841c616f8c0
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>如何：從命令列中選取要使用的負載測試回合設定

負載測試可以包含一個或多個「回合設定」，這是指一組會影響負載測試執行方式的屬性。 這些設定會在 [屬性] 視窗中，依照分類進行組織。 負載測試執行時，它會使用目前設為使用中的回合設定。

 如果您的負載測試只包含一個回合設定，該設定一律為使用中的節點。 如果您的負載測試包含多個回合設定節點，則可以從命令列選取要在執行負載測試時使用的節點。 請參閱[如何：將其他回合設定新增至負載測試](../test/how-to-add-additional-run-settings-to-a-load-test.md)。

## <a name="to-change-the-run-setting-from-the-command-line"></a>若要從命令列變更回合設定

1.  如果您想要從命令列使用不同的回合設定來運用內容參數策略，請使用下列命令：

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2.  使用 mstest 執行負載測試：

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>另請參閱

- [設定負載測試回合設定](../test/configure-load-test-run-settings.md)
- [在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [如何：將其他回合設定新增至負載測試](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [如何：選取負載測試的使用中回合設定](../test/how-to-select-the-active-run-setting-for-a-load-test.md)