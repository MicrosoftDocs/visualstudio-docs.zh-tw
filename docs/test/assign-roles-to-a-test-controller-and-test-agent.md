---
title: 測試控制器和測試代理程式角色
description: 瞭解如何建立和設定測試設定，以使用測試控制器和測試代理程式，透過 Visual Studio 將測試分散到多部電腦上。
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c059510dc39472d5c981f93e4d7259545b809d38
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442439"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>將角色指派至測試控制器和測試代理程式

本文將示範如何建立和設定測試設定，讓這個測試設定透過測試控制器和測試代理程式，使用 Visual Studio 將測試分散到多部電腦。 它也會示範如何將診斷和資料配接器新增到測試設定。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>必要條件

- 建立要使用測試設定執行的單元測試或自動程式碼 UI 測試。

- 安裝測試控制器和測試代理程式。 如需如何安裝測試控制器和測試代理程式的資訊，請參閱[安裝並設定測試代理程式](../test/lab-management/install-configure-test-agents.md)。

## <a name="to-create-and-configure-a-test-setting"></a>若要建立和設定測試設定

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **方案專案]，** 指向 [ **加入**]，然後選擇 [ **新增專案**]。

     [加入新項目]  對話方塊隨即出現。

2. 在 [安裝的範本] 窗格中，選擇 [測試設定]。

3. 在 [名稱] 方塊中鍵入 **TestSettingDistributedTestWalkthrough**。

4. 選擇 [新增]  。

     新測試 *TestSettingDistributedTestWalkthrough.testsettings* 檔案會出現在 [方案總管] 的 [方案項目] 資料夾底下。

     [測試設定] 對話方塊隨即顯示。 已選取 [一般] 頁面。

     接著，便可以編輯和儲存測試設定值。

5. 在 [名稱] 下方鍵入測試設定的名稱。

6. 在 [描述] 底下，鍵入 **分散式測試設定**。

7. 將 [預設命名配置] 保持選取狀態。

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>若要將角色指派至測試控制器和測試代理程式

1. 選擇 **[角色]**。

     [角色] 頁面隨即顯示。

2. 若要遠端執行測試，請使用 [測試執行方法] 下拉式清單並選取 [遠端執行]。

3. 在 [控制器]下拉式清單中，鍵入[您的測試控制器](../test/lab-management/install-configure-test-agents.md)電腦名稱。

    > [!NOTE]
    > 如果這是您第一次加入控制器，下拉式清單不會列出任何控制器。 您先前在其他測試設定中指定的控制器會填入此清單中。

4. 在 [角色] 底下選擇 [新增]。

5. 在 [名稱] 欄底下的反白顯示列，鍵入 **分散式測試**。

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>若要將診斷和資料配接器指派至測試設定

1. 選擇 [資料和診斷]。

     [資料和診斷] 頁面隨即顯示。

2. 在 [角色] 底下，確認已選取 **分散式測試** 角色。

3. 在 [所選角色的資料和診斷] 底下，選取 [IntelliTrace] 和 [系統資訊] 配接器。

     如需這些配接器以及可用於測試設定之其他配接器的資訊，請參閱[設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)。

4. 選擇 [主機]。

5. (選擇性) 如果您電腦執行的是 64 位元版本的 Microsoft Windows，而且您使用 [任何 CPU] 組態來編譯測試，請使用 [在 32 位元或 64 位元處理序中執行測試] 下拉式清單並選取 [在 64 位元電腦上的 64 位元處理序中執行測試]。

    > [!TIP]
    > 為了達到最大彈性，您應該使用 [任何 CPU] 組態來編譯測試專案。 然後，您就可以在 32 位元和 64 位元代理程式上執行。 使用 [64 位元] 組態來編譯測試專案並沒有任何優點。

6. 若要儲存新的測試設定，請選擇 [套用]。

7. 選擇 [關閉]。

::: moniker range="vs-2017"

8. 在 [ **測試** ] 功能表上，選取 [ **測試設定**] > **選取 [測試組態檔** ]，然後選擇 *testsettingdistributedtestwalkthrough.testsettings .testsettings* 檔案。

::: moniker-end

::: moniker range=">=vs-2019"

8. 在 [ **測試** ] 功能表上，選擇 [ **選取設定檔**]。 瀏覽並選取 *TestSettingDistributedTestWalkthrough.testsettings* 檔案。

::: moniker-end

9. 以平常的方式執行測試。

     當測試控制器處理單元測試和自動程式碼 UI 測試時，測試控制器會以 100 為單位，將這些測試分成群組，然後將它們傳送至測試代理程式電腦。 例如，如果您有 250 個單元測試和三個測試代理程式，前 100 個單元測試將傳送至代理程式 1、後 100 個單元測試將傳送至代理程式 2，而其餘 50 個單元測試則傳送至代理程式 3。

## <a name="see-also"></a>另請參閱

- [安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)
