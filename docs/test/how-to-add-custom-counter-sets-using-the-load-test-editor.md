---
title: 新增用於負載測試的自訂計數器集合
description: 當您使用 [負載測試精靈] 建立負載測試時，您會加入初始的計數器集合。 瞭解如何使用負載測試編輯器新增自訂計數器集合。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: ce34a4e30c9d612bd37afb61c354b7a4b5df7aed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966925"
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>如何：使用負載測試編輯器新增自訂計數器集合

當您使用 [新增負載測試精靈] 建立負載測試時，會新增初始的計數器集合。 這些都會為您的負載測試提供一組預先定義的計數器集合。

> [!NOTE]
> 如果您的負載測試已分配給遠端電腦，控制器和代理程式計數器就會對應至控制器和代理程式計數器集合。 如需如何在負載測試中使用遠端電腦的詳細資訊，請參閱[測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)。

請在 [負載測試編輯器] 中管理計數器。 您可以在負載測試的 [計數器集合] 節點中，看到已新增至測試的計數器集合。 當您建立負載測試之後，可以將新的自訂計數器集合加入至其中。

![自訂計數器集合](../test/media/loadtestcustomcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>將自訂計數器集合加入至負載測試

1. 開啟負載測試。

2. 展開 [計數器集合] 節點。 您可以在這個節點中看到已加入至負載測試的所有計數器集合。

3. 以滑鼠右鍵按一下 [計數器集合] 節點，然後選取 [新增自訂計數器集合]。

    > [!NOTE]
    > 計數器集合會命名為預設名稱，例如 **Custom1**。 您可以使用 [屬性] 視窗變更名稱。 按 **F4** 顯示 [屬性] 視窗。

4. 若要將計數器新增至自訂計數器集合，請以滑鼠右鍵按一下新的計數器集合，然後選擇 [新增計數器]。 如需如何新增計數器的詳細資訊，請參閱[如何：將計數器新增至計數器集合](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)。

    > [!NOTE]
    > 另一個加入自訂計數器集合的方法是，以滑鼠右鍵按一下現有的計數器集合，選擇 [複製]，然後將它貼至 [計數器集合] 節點。 如果也複製了其他不需要的計數器，可以予以刪除。 您可以使用 [屬性] 視窗變更新計數器集合的名稱。

## <a name="see-also"></a>另請參閱

- [在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [設定負載測試回合設定](../test/configure-load-test-run-settings.md)
