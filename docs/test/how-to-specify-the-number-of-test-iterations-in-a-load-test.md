---
title: 在負載測試回合設定中指定測試反覆項目的數目
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 446da348c1a947e6c59b8ad60d9bd0799d0d4322
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588937"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>如何：在負載測試回合設定中指定測試反覆項目的數目

使用 [新增負載測試精靈]**** 建立負載測試之後，您就可以使用 [負載測試編輯器]**** 來變更情節屬性，以便符合您的測試需求和目標。 有關詳細資訊，請參閱[演練：創建並運行負載測試](../test/walkthrough-create-and-run-a-load-test.md)。

使用**負載測試編輯器**，可以在屬性視窗中編輯回合設定值的 **"測試反覆運算"****屬性**。 測試**反覆運算**屬性指定使用**負載測試編輯器**在負載測試中的所有方案中在所有 Web 性能和單元測試中運行的反覆運算數。

> [!NOTE]
> 如需回合設定屬性及其描述的完整清單，請參閱[負載測試回合設定屬性](../test/load-test-run-settings-properties.md)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>若要在回合設定中指定測試反覆項目的數目

1. 開啟負載測試。

     [負載測試編輯器]**** 隨即出現，並顯示負載測試樹狀目錄。

2. 在負載測試樹狀目錄的 [回合設定]**** 資料夾中，選擇回合設定。

3. 在 [檢視]**** 功能表上，選取 [屬性視窗]**** 以檢視負載回合設定的分類和屬性。

4. 將 [使用測試反覆項目]**** 屬性設為 [True]****。

5. 在 [測試反覆項目]**** 屬性中，輸入數字表示在負載測試期間要執行的測試反覆項目數。

6. 屬性變更完成之後，選擇 [檔案]**** 功能表上的 [儲存]****。 然後，您就可以使用新的 [測試反覆項目]**** 值來執行負載測試。

## <a name="see-also"></a>另請參閱

- [配置負載測試回合設定](../test/configure-load-test-run-settings.md)
- [負載測試情節屬性](../test/load-test-scenario-properties.md)
