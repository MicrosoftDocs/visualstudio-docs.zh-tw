---
title: 將計數器新增至計數器集合以進行負載測試
description: 當您使用 [負載測試精靈] 建立負載測試時，您會加入初始的計數器集合。 瞭解如何使用負載測試編輯器來新增計數器。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6aabd5bc7293a73ec0fa1a304262c24776a9e38f
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442569"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>如何：使用負載測試編輯器將計數器新增至計數器集合

當您使用 [負載測試精靈] 建立負載測試時，您會新增初始的計數器集合。 這些都會為您的負載測試提供一組預先定義的計數器集合。 如需詳細資訊，請參閱[在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> 如果您的負載測試已分配給遠端電腦，控制器和代理程式計數器就會對應至控制器和代理程式計數器集合。 如需如何在負載測試中使用遠端電腦的詳細資訊，請參閱[測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)。

請在 [負載測試編輯器] 中管理計數器。 您可以在負載測試的 [計數器集合] 節點中，看到已新增至測試的計數器集合。 當您建立負載測試之後，可以將新的計數器加入至現有的計數器集合。

## <a name="to-add-counters-to-a-counter-set"></a>將計數器加入至計數器集合

1. 開啟負載測試。

2. 展開 [計數器集合] 節點。 您可以在這個節點中看到已加入至負載測試的所有計數器集合。

    > [!NOTE]
    > 負載測試階層樹狀結構中也包含了 [回合設定] 節點。 這個節點包含 [計數器集合對應] 節點，後者會顯示所有電腦，以及對應至這些電腦的計數器集合。

3. 以滑鼠右鍵按一下現有的計數器集合，然後選擇 [新增計數器]。

     [選取效能計數器] 對話方塊隨即出現。

4. 在 [電腦] 下拉式方塊中，鍵入您要對應的電腦名稱。 或者，在下拉式清單中選取其中一個電腦名稱。

    > [!NOTE]
    > 因為計數器集合必須在收集效能資料之前對應至電腦，因此必須指定要收集效能資料的電腦。

5. 請選取 [效能分類] 來選效能資料計數器的分類。 您將會看到兩個可以從中選取效能計數器的資料行。

    > [!NOTE]
    > 有些計數器類別會要求您同時選取執行個體。 例如，如果您選取 SQL 計數器，則必須選取 SQL 執行個體，因為目標電腦上可能安裝了一個以上的 SQL 執行個體。

6. 請選取計數器和執行個體，以加入至自訂計數器集合。

     \- 或 -

     選取 [所有計數器] 選項按鈕，選取所有可用的計數器。

7. 選擇 [確定]。

    > [!NOTE]
    > 另一個將計數器加入至計數器集合的方法是，選擇現有的計數器或計數器類別，選擇 [複製]，然後將它們貼至另一個計數器集合節點。 如果也複製了其他不需要的計數器，可以予以刪除。

## <a name="see-also"></a>另請參閱

- [在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [設定負載測試回合設定](../test/configure-load-test-run-settings.md)
