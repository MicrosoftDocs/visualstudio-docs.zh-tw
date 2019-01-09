---
title: 將角色指派給測試控制器和測試代理程式，以便進行自動化測試
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: a3904efd69763a096504922ee233a927ba69ed8f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847031"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>將角色指派至測試控制器和測試代理程式

本逐步解說將示範如何建立和設定測試設定，讓這個測試設定透過測試控制器和測試代理程式使用 Visual Studio 將測試分散到多部電腦。 此外，本逐步解說也會示範如何將診斷和資料配接器加入至測試設定。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>必要條件

-   建立要使用測試設定執行的單元測試或自動程式化 UI 測試。

-   安裝測試控制器和測試代理程式。 如需如何安裝測試控制器和測試代理程式的資訊，請參閱[安裝並設定測試代理程式](../test/lab-management/install-configure-test-agents.md)。

## <a name="to-create-and-configure-a-test-setting"></a>若要建立和設定測試設定

1.  在 [方案總管] 中，以滑鼠右鍵按一下 [方案項目]、指向 [新增]，然後選擇 [新增項目]。

     [新增項目] 對話方塊隨即出現。

2.  在 [安裝的範本] 窗格中，選擇 [測試設定]。

3.  在 [名稱] 方塊中鍵入 **TestSettingDistributedTestWalkthrough**。

4.  選擇 [新增]。

     新測試 *TestSettingDistributedTestWalkthrough.testsettings* 檔案會出現在 [方案總管] 的 [方案項目] 資料夾底下。

     [測試設定] 對話方塊隨即顯示。 已選取 [一般] 頁面。

     接著，便可以編輯和儲存測試設定值。

    > [!NOTE]
    > 您所建立的每個測試設定，都會列為 [測試] 功能表上 [選取現用測試設定] 和 [編輯測試設定] 選項的選擇。

5.  在 [名稱] 下方鍵入測試設定的名稱。

6.  在 [描述] 底下，鍵入**分散式測試設定**。

7.  將 [預設命名配置] 保持選取狀態。

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>若要將角色指派至測試控制器和測試代理程式

1.  選擇 [角色]。

     [角色] 頁面隨即顯示。

2.  若要遠端執行測試，請使用 [測試執行方法] 下拉式清單並選取 [遠端執行]。

3.  在 [控制器]下拉式清單中，鍵入[您的測試控制器](../test/lab-management/install-configure-test-agents.md)電腦名稱。

    > [!NOTE]
    > 如果這是您第一次加入控制器，下拉式清單不會列出任何控制器。 您先前在其他測試設定中指定的控制器會填入此清單中。

4.  在 [角色] 底下選擇 [新增]。

5.  在 [名稱] 欄底下的反白顯示列，鍵入**分散式測試**。

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>若要將診斷和資料配接器指派至測試設定

1.  選擇 [資料和診斷]。

     [資料和診斷] 頁面隨即顯示。

2.  在 [角色] 底下，確認已選取**分散式測試**角色。

3.  在 [所選角色的資料和診斷] 底下，選取 [IntelliTrace] 和 [系統資訊] 配接器。

     如需這些配接器以及可用於測試設定之其他配接器的資訊，請參閱[設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)。

4.  選擇 [主機]。

5.  (選擇性) 如果您電腦執行的是 64 位元版本的 Microsoft Windows，而且您使用 [任何 CPU] 組態來編譯測試，請使用 [在 32 位元或 64 位元處理序中執行測試] 下拉式清單並選取 [在 64 位元電腦上的 64 位元處理序中執行測試]。

    > [!TIP]
    > 為了達到最大彈性，您應該使用 [任何 CPU] 組態來編譯測試專案。 然後，您就可以在 32 位元和 64 位元代理程式上執行。 使用 [64 位元] 組態來編譯測試專案並沒有任何優點。

6.  若要儲存新的測試設定，請選擇 [套用]。

7.  選擇 [關閉]。

8.  在 [測試] 功能表上選取 [選取現用測試設定]，然後選擇 [TestSettingDistributedTestWalkthrough.testsettings]。

9. 以平常的方式執行測試。

     當測試控制器處理單元測試和自動程式化 UI 測試時，測試控制器會以 100 為單位，將這些測試分成群組，然後將它們傳送至測試代理程式電腦。 例如，如果您有 250 個單元測試和三個測試代理程式，前 100 個單元測試將傳送至代理程式 1、後 100 個單元測試將傳送至代理程式 2，而其餘 50 個單元測試則傳送至代理程式 3。

## <a name="see-also"></a>另請參閱

- [安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)