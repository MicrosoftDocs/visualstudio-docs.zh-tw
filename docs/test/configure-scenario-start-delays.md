---
title: 設定負載測試的情節啟動延遲
description: 瞭解如何使用負載測試編輯器和屬性視窗，在負載測試中指定情節啟動之前的延遲。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: bc7a57e759cbeb6fcb5fd9c96dd4c68aa0637afa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868032"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>在負載測試中設定情節啟動延遲

您可以使用 [負載測試編輯器] 和 [屬性] 視窗，在負載測試中指定情節啟動之前的延遲。

比方說，如果您需要某個情節開始產生另一個情節會使用的項目，則可能需要使用 [延遲開始時間] 屬性。 您可以延遲使用項目的情節，讓產生項目的情節可以填入一些資料。

而某個情節只能在一天中的特定時間中執行，這是另一個範例。 因此，您要延遲啟動情節以同步進行此項作業。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>指定情節的延遲開始時間

您可以使用 [負載測試編輯器] 來變更 [屬性] 視窗中的 [延遲開始時間] 屬性，藉以指定在負載測試中啟動情節之前的延遲。

> [!NOTE]
> 如需負載測試情節屬性及其描述的完整清單，請參閱 [負載測試情節屬性](../test/load-test-scenario-properties.md)。

當您需要某個情節開始產生另一個情節會使用的項目時，就是您可能會想要使用 [延遲開始時間] 屬性的其中一個執行個體範例。 您可以延遲使用項目的情節，讓產生項目的情節可以填入一些資料。

此外，您可能會有某個只在一天中特定時間執行的情節，而這是另一個範例。 因此，您想要延遲啟動情節以模擬這種情況。

> [!NOTE]
> 如需回合設定屬性及其描述的完整清單，請參閱[負載測試情節屬性](../test/load-test-scenario-properties.md)。

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>若要指定情節的延遲開始時間

1. 開啟負載測試。

     [負載測試編輯器] 隨即出現。 負載測試樹狀結構隨即顯示。

2. 在負載測試樹狀目錄的 [情節] 資料夾中，選擇您想要指定延遲開始時間的情節節點。

3. 在 [檢視] 功能表上，選取 [屬性視窗]。

     情節的分類和屬性會顯示在 [屬性] 視窗中。

4. 在 [延遲開始時間] 屬性的文字方塊中鍵入時間值，這個時間值會指出執行負載測試時，在負載測試開始之後及啟動情節之前所等待的時間。

    > [!NOTE]
    > 如果情節的 [準備期間停用] 屬性值設定為 [True]，則 [延遲開始時間] 屬性的時間值在準備期間之後便會套用。 您可以使用 [準備期間停用] 情節屬性，來控制準備時要併入的情節。

5. 變更屬性之後，請選擇 [檔案] 功能表上的 [儲存]。 然後，您就可以使用新的 [延遲開始時間] 值來執行負載測試。

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>啟用和停用熱身期間是否要執行情節

[熱身期間停用] 屬性是使用 [屬性] 視窗來設定。 編輯負載測試情節屬性是由 [負載測試編輯器] 設定。

[準備期間停用] 屬性是用來指示在 [延遲開始時間] 屬性中指定的準備期間是否應該執行情節。 如需詳細資訊，請檢閱前一個程序[指定情節的延遲開始時間](#specify-the-delay-start-time-of-a-scenario)。

> [!NOTE]
> 如需回合設定屬性及其描述的完整清單，請參閱[負載測試情節屬性](../test/load-test-scenario-properties.md)。

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>若要針對情節啟用或停用準備期

1. 開啟負載測試。

     [負載測試編輯器] 隨即出現。 負載測試樹狀結構隨即顯示。

2. 在負載測試樹狀目錄的 [情節] 資料夾中，選擇您要變更其準備行為的情節節點。

3. 在 [檢視] 功能表上，選取 [屬性視窗]。

     情節的分類和屬性會顯示在 [屬性] 視窗中。

     在 [準備期間停用] 屬性中選取 [True] 或 [False]。

4. 屬性變更完成之後，選擇 [檔案] 功能表上的 [儲存]。 然後，您就可以使用新的 [準備期間停用] 值來執行負載測試。

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
- [設定用於負載測試的測試代理程式和測試控制器](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [負載測試情節屬性](../test/load-test-scenario-properties.md)
