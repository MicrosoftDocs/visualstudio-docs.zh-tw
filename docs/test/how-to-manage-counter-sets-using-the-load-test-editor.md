---
title: 負載測試計數器集合
description: 瞭解如何藉由選擇電腦並指派要從每部電腦收集的計數器集合，來使用負載測試編輯器管理管理計數器集合。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.dialog.countersetmapping
helpviewer_keywords:
- counters, counter sets
- performance counters
- counter sets
- load tests, counter sets
ms.assetid: 64315c2f-a0b2-4378-be16-0774b99beef5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 684715ed8ac29a3c85d0ea46799a2e14fb9722bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961439"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>如何：使用負載測試編輯器管理計數器集合

當您使用 [新增負載測試精靈] 建立負載測試時，會新增初始的計數器集合。 這些都會為您的負載測試提供一組預先定義的計數器集合。

> [!NOTE]
> 如果您的負載測試已分配給遠端電腦，控制器和代理程式計數器就會對應至控制器和代理程式計數器集合。 如需如何在負載測試中使用遠端電腦的詳細資訊，請參閱[測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)。

對應計數器集合包含選擇您要從中收集效能資料的電腦集合，並指派一組計數器集合收集每一部個別電腦。 請在 [負載測試編輯器] 中管理計數器。

![管理計數器集合](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>管理計數器集合

1. 開啟負載測試。

2. 選擇 [管理計數器集合] 按鈕。

     -或-

     以滑鼠右鍵按一下負載測試樹狀目錄中的 [計數器集合] 資料夾，然後選擇 [管理計數器集合]。

     [管理計數器集合] 對話方塊隨即顯示。

3. (選擇性) 在 [選取的電腦和計數器集合會新增至下列回合設定之下] 清單方塊中，選取不同的回合設定。

    > [!NOTE]
    > 這僅適用於您的負載測試中有一個以上的回合設定時。

4. (選擇性) 選擇 [新增電腦]，新增要監視的新電腦。 系統會提示輸入名稱， 輸入電腦名稱後，您將會在新項目下方看到節點。 例如，**ASP.NET**、**IIS**、**SQL** 等等。 選取您要選取之節點前方的核取方塊。 新的計數器隨即出現在 [預覽選取範圍] 窗格中。

5. (選擇性) 在 [電腦標記] 文字方塊中，鍵入要與電腦產生關聯的標記。 例如，"TestMachine12 in lab3"。

     電腦標記可讓您使用容易辨識的名稱來識別電腦。

     這些標記會顯示在 [負載測試編輯器] 樹狀目錄的 [計數器集合對應] 節點中。 更重要的是，這些標記會顯示在 Excel 報表中，可協助專案關係人識別電腦在負載測試中扮演的角色。 例如 "Web Server1 in lab2" 或 "SQL Server2 in Phoenix office"。 如需詳細資訊，請參閱[針對測試比較或趨勢分析報告負載測試結果](../test/compare-load-test-results.md)。

6. 選擇 [確定]。

## <a name="see-also"></a>另請參閱

- [測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)
- [在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [設定負載測試回合設定](../test/configure-load-test-run-settings.md)
