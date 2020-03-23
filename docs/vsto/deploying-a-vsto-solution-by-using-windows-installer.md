---
title: 使用 Windows 安裝程式部署用於辦公室解決方案的視覺化工作室工具
ms.date: 08/18/2010
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 876781cb6967f5d10dddccd54a46e218170445ab
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432361"
---
# <a name="deploying-a-visual-studio-tools-for-office-solution-using-windows-installer"></a>使用 Windows 安裝程式部署用於辦公室解決方案的視覺化工作室工具

## <a name="summary"></a>摘要

瞭解如何使用視覺化工作室安裝程式專案部署適用于 Office （VSTO） 的 Microsoft 視覺化工作室工具外接程式或文檔級解決方案。

伍特·范·武格特，代碼顧問

泰德·帕蒂森，泰德·帕蒂森集團

本文由 Microsoft 在原始作者的許可下更新。

**適用于：** 辦公室視覺工作室工具，微軟辦公室，微軟視覺工作室。

## <a name="overview"></a>概觀

您可以使用 Windows 安裝程式包開發 VSTO 解決方案並部署解決方案。 此討論包括部署簡單 Office 外接程式的步驟。

## <a name="deployment-methods"></a>部署方法

ClickOnce 可輕鬆用於為載入項和解決方案創建設置。 但是，它無法安裝需要管理許可權（如電腦級載入項）的載入項。

可以使用 Windows 安裝程式安裝需要管理許可權的載入項，但創建安裝程式確實需要付出更多努力。

有關如何使用 ClickOnce 部署 VSTO 解決方案的概述，請參閱[使用 ClickOnce 部署 Office 解決方案](deploying-an-office-solution-by-using-clickonce.md)。

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>部署面向 VSTO 運行時的 Office 解決方案

按一下"一次"和"Windows 安裝程式"包需要在安裝 Office 解決方案時執行相同的基本任務。

1. 在使用者電腦上安裝必備元件。
2. 部署解決方案的特定元件。
3. 對於外接程式，請創建登錄機碼。
4. 信任解決方案以允許其執行。

### <a name="required-prerequisite-components-on-the-target-computer"></a>目的電腦上的必需先決條件元件

下面是電腦上必須安裝的軟體清單才能運行 VSTO 解決方案：

- 微軟 Office 2010 或更新。
- 微軟 .NET 框架 4 或更新。
- Microsoft Visual Studio 2010 Tools for Office Runtime。
  運行時提供了一個管理載入項和文檔級解決方案的環境。 運行時的版本確實隨 Microsoft Office 一起發佈，但您可能希望使用外接程式重新分發特定版本。
- 如果您不使用嵌入式互操作類型，則為 Microsoft Office 的主交互操作程式集。
- 專案引用的任何實用程式程式集。

### <a name="specific-components-for-the-solution"></a>解決方案的特定元件

安裝套裝程式必須將這些元件安裝到使用者的電腦：

- 如果創建文檔級解決方案，則為 Microsoft Office 文檔。
- 自訂程式集及其所需的任何程式集。
- 其他元件，如設定檔。
- 應用程式清單 （.清單）。
- 部署清單 （.vsto）。

### <a name="registry-entries-for-add-ins"></a>外接程式的登錄機碼

Microsoft Office 使用登錄機碼查找和載入載入載入載入項。這些登錄機碼應作為部署過程的一部分創建。 有關這些登錄機碼的詳細資訊，請參閱[VSTO 載入項的登錄機碼](registry-entries-for-vsto-add-ins.md)。

顯示自訂表單區域的 Outlook 增益集需要允許標識表單區域的其他登錄機碼。 有關登錄機碼的詳細資訊，請參閱[Outlook 表單區域的登錄機碼](registry-entries-for-vsto-add-ins.md#OutlookEntries)。

文檔級解決方案不需要任何登錄機碼。 相反，文檔內的屬性用於查找自訂項。 有關這些屬性的詳細資訊，請參閱[自訂文件屬性概述](custom-document-properties-overview.md)。

### <a name="trusting-the-vsto-solution"></a>信任 VSTO 解決方案

為了運行自訂項，電腦必須信任解決方案。 可以通過使用證書對清單進行簽名、創建包含清單的信任關係或將其安裝到電腦上的受信任位置來信任外接程式。

有關如何獲取簽章憑證的詳細資訊，請參閱[按一下"一次部署"和"身份驗證"。](../deployment/clickonce-and-authenticode.md) 有關信任解決方案的詳細資訊，請參閱[使用包含清單信任辦公室解決方案](trusting-office-solutions-by-using-inclusion-lists.md)。 您可以在 Windows 安裝程式檔中添加包含清單條目，並包含自訂操作。 有關啟用包含清單的詳細資訊，請參閱[如何：配置包含清單安全性](how-to-configure-inclusion-list-security.md)。

如果未使用這兩個選項，則向使用者顯示信任提示，以讓他們決定是否信任解決方案。

有關與文檔級解決方案相關的安全性的詳細資訊，請參閱[授予文檔信任](granting-trust-to-documents.md)。

## <a name="creating-a-basic-installer"></a>創建基本安裝程式

"設置"和"部署"專案範本包含在可供下載的[Microsoft 視覺化工作室安裝程式專案](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects)擴展中。

要為 Office 解決方案創建安裝程式，必須完成以下任務：

- 添加將部署的 Office 解決方案的元件。
- 對於應用程式級載入項，請配置登錄機碼。
- 配置必備元件，以便可以在最終使用者電腦上安裝這些元件。
- 配置啟動條件以驗證所需的必備元件是否可用。 如果未安裝所有必需的先決條件，則啟動條件可用於阻止安裝。

第一步是創建設置專案。

### <a name="to-create-the-addin-setup-project"></a>創建添加設置專案

1. 打開要部署的 Office 添加專案。 在此示例中，我們使用名為 ExcelAddIn 的 Excel 外接程式。
2. 打開"辦公室專案"後，在 **"檔**"功能表上展開 **"添加"，** 然後按一下 **"新專案**"以添加新專案。
::: moniker range="=vs-2017"
3. 在"**添加新專案"** 對話方塊中，在 **"專案類型"** 窗格中展開**其他專案類型**，然後展開 **"設置和部署"，** 然後選擇**視覺化工作室安裝程式**。
4. 在 **"範本"** 窗格中，從**視覺化工作室安裝**的範本組中選擇 **"設置專案**"。
::: moniker-end
::: moniker range="=vs-2019"
3. 在"**添加新專案**"對話方塊中，選擇 **"設置專案"** 範本。
4. 按 [下一步]****。
::: moniker-end

5. 在 **"名稱**"框中，鍵入**OfficeAddInsetup**。
::: moniker range="=vs-2017"
6. 按一下 **"打開"** 以創建新的設置專案。
::: moniker-end
::: moniker range="=vs-2019"
6. 按一下 **"創建**"以創建新的設置專案。
::: moniker-end

視覺化工作室為新的設置專案打開檔案系統資源管理器。 檔案系統資源管理器允許您將檔添加到設置專案。

   ![設置專案的檔案系統資源管理器螢幕截圖](media/setup-project-figure-1.png)

   **圖 1：設置專案的檔案系統資源管理器**

安裝程式專案需要部署 ExcelAddIn。 您可以通過將 ExcelAddIn 專案輸出添加到安裝程式專案來配置此任務的設置專案。

### <a name="to-add-the-exceladdin-project-output"></a>添加 ExcelAddIn 專案輸出

1. 在**解決方案資源管理器**中，按右鍵**OfficeAddInSetup**，按一下 **"添加**"，然後按一下 **"專案輸出**"。
2. 在 **"添加專案輸出組"** 對話方塊中，從專案清單中選擇**ExcelAddIn**和**主輸出**。
3. 按一下"**確定"** 將專案輸出添加到設置專案。

    ![設置專案添加專案輸出組對話方塊的螢幕截圖](media/setup-project-figure-2.png)

    **圖 2：設置專案 添加專案輸出組對話方塊**

安裝程式專案需要部署部署清單和應用程式清單。 從 ExcelAddIn 專案的輸出檔案夾中將這兩個檔作為獨立檔添加到安裝程式專案中。

### <a name="to-add-the-deployment-and-application-manifests"></a>添加部署和應用程式清單

1. 在**解決方案資源管理器**中，按右鍵**OfficeAddInSetup，** 按一下"**添加**"，然後按一下"**檔**"。
2. 在"**添加檔"** 對話方塊中，導航到**ExcelAddIn**輸出目錄。 通常，輸出目錄是專案根目錄的**bin\\發佈**子資料夾，具體取決於所選的組建組態。
3. 選擇**ExcelAddIn.vsto**和**ExcelAddIn.dll.清單**檔，然後按一下 **"打開"** 以將這兩個檔添加到設置專案中。

    ![應用程式和部署清單的螢幕截圖在解決方案資源管理器中](media/setup-project-figure-3.jpg)

    **圖 3：解決方案資源管理器中外接程式的應用程式和部署清單**

引用 ExcelAddIn 包括 ExcelAddIn 需要的所有元件。 必須排除這些元件並使用先決條件包進行部署，以允許正確註冊它們。 此外，在安裝開始之前，必須顯示並接受軟體授權條款。

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>排除 ExcelAddIn 專案依賴項

1. 在**解決方案資源管理器**中，在**OfficeAddInSetup**節點中，選擇 **"檢測到的依賴項"** 項下的所有依賴項項，但**Microsoft .NET 框架**或任何以**\*結尾的程式集除外。公用事業.dll**. 實用程式程式集旨在與應用程式一起部署。
2. 按右鍵組並選擇 **"屬性**"。
3. 在 **"屬性"** 視窗中，將 **"排除"** 屬性更改為**True**以從設置專案中排除依存性程式集。 確保不排除任何實用程式程式集。

    ![解決方案資源管理器的螢幕截圖，顯示要排除的依賴項](media/setup-project-figure-4.jpg)

    **圖 4：排除依賴項**

您可以通過添加安裝程式（也稱為引導程式）來配置 Windows 安裝程式包以安裝必備元件。 此設置程式可以安裝先決條件元件，此過程稱為引導。

對於**ExcelAddIn，** 必須先安裝這些先決條件，然後才能正確運行外接程式：

- Office 解決方案所針對的 Microsoft .NET 框架版本。
- Microsoft Visual Studio 2010 Tools for Office 執行階段。

將從屬元件配置為先決條件

1. 在**解決方案資源管理器**中，按右鍵**OfficeAddInSetup**專案並選擇**屬性**。
2. 將顯示 **"OfficeAddInSetup 屬性頁**"對話方塊。
3. 按一下 **"先決條件"** 按鈕。
4. 在"先決條件"對話方塊中，選擇正確的版本的 .NET 框架和適用于 Office 運行時的 Microsoft 視覺化工作室工具。

    ![先決條件對話方塊的螢幕截圖](media/setup-project-figure-5.png)

    **圖 5：先決條件對話方塊**

    > [!NOTE]
    >視覺化工作室安裝程式專案中已配置的一些必備包取決於所選的組建組態。 您必須為使用的每個組建組態選擇正確的必備元件。

Microsoft Office 使用登錄機碼查找載入項。 HKEY\_CURRENT\_使用者配置單元中的鍵用於為每個使用者註冊外接程式。 HKEY\_LOCAL\_MACHINE 配置單元下的鍵用於為電腦的所有使用者註冊外接程式。 有關登錄機碼的詳細資訊，請參閱[VSTO 載入項的登錄機碼](registry-entries-for-vsto-add-ins.md)。

### <a name="to-configure-the-registry"></a>配置註冊表

1. 在**解決方案資源管理器**中，按右鍵**OfficeAddInSetup**。
2. 展開**視圖**。
3. 按一下**註冊表**以打開登錄編輯程式視窗。
4. 在**註冊表（OfficeAddInSetup）編輯器中**，展開**HKEY\_LOCAL\_MACHINE，** 然後**展開軟體**。
5. 刪除在**\[ \] ** **HKEY\_LOCAL\_MACHINE\\軟體**下找到的製造商金鑰 。
6. 擴展**\_HKEY\_CURRENT 使用者**，然後**擴展軟體**。
7. 刪除在**\[ \] ** **HKEY\_CURRENT\_USER\\軟體**下找到的製造商金鑰。
8. 要添加外接程式安裝的登錄機碼，請按右鍵 **"使用者/電腦 Hive"** 鍵，請選擇 **"新建金鑰**"。 使用文本**軟體**為新金鑰的名稱。 右鍵點擊新創建**的軟體**金鑰，並創建一個新的金鑰與文本**微軟**。
9. 使用類似的過程創建外接程式註冊所需的整個金鑰層次結構：

    **\\使用者/機器蜂巢軟體\\微軟\\辦公室\\\\Excel 載入\\項示例公司.ExcelAddIn**

    公司名稱通常用作外接程式名稱的首碼，以提供唯一性。

10. 按右鍵**示例公司.ExcelAddIn**鍵，選擇 **"新建**"，然後按一下**字串值**。 使用名稱的文本**說明**。
11. 使用此步驟可以添加另外三個值：
    - 類型**字串**的**易記名稱**
    - **DWORD**類型的**載入行為**
    - 類型**字串****的清單**

12. 按右鍵登錄編輯程式中的 **"描述"** 值，然後按一下 **"屬性視窗**"。 在 **"屬性"視窗中**，為"值"屬性輸入**Excel 演示添加。**
13. 在登錄編輯程式中選擇 **"易記名稱**"鍵。 在**屬性視窗中**，將**值**屬性更改為**Excel 演示添加。**
14. 在登錄編輯程式中選擇**LoadBehavior**鍵。 在 **"屬性"視窗中**，將 **"值"** 屬性更改為**3。** LoadBehavior 的值 3 指示應在啟動主機應用程式時載入外接程式。 有關載入行為的詳細資訊，請參閱[VSTO 載入項的登錄機碼](registry-entries-for-vsto-add-ins.md)。

15. 在登錄編輯程式中選擇 **"清單**"鍵。 在 **"屬性"視窗中**，將 **"值"** 屬性更改為**檔：//[目標ID_ExcelAddIn.vsto_vsto）本地**

    ![登錄編輯程式的螢幕截圖](media/setup-project-figure-6.png)

    **圖 6：設置登錄機碼**

      VSTO 運行時使用此登錄機碼來查找部署清單。 [目標]宏將替換為將外接程式安裝到的資料夾。 宏將包含尾隨的 * 字元，因此部署清單的檔案名應為 ExcelAddIn.vsto，而不顯示 * 字元。
      **vstolocal**尾碼告訴 VSTO 運行時，外接程式應從此位置載入，而不是 ClickOnce 緩存。 刪除此後修復程式將導致運行時將自訂項複製到 ClickOnce 緩存中。

   >[!WARNING]
   >您應該非常小心在視覺化工作室的登錄編輯程式。 例如，如果您不小心為錯誤的金鑰設置了 DeleteAtUn 安裝，則可以刪除註冊表的活動部分，從而使使用者電腦處於不一致甚至更糟的損壞狀態。

64 位版本的 Office 將使用 64 位註冊表配置單元來查找載入項。要在 64 位註冊表配置單元下註冊載入項，必須僅將安裝程式專案的目標平臺設置為 64 位。

1. 在解決方案資源管理器中選擇**OfficeAddInSetup**專案。
2. 轉到 **"屬性"** 視窗並將**TargetPlatform**屬性設置為**x64**。

為 32 位和 64 位版本的 Office 安裝外接程式需要創建兩個單獨的 MSI 包。 一個用於 32 位，一個用於 64 位。

  ![屬性視窗的螢幕截圖，顯示用於向 64 位 Office 註冊載入項的目標平臺](media/setup-project-figure-7.jpg)

  **圖 7：用於在 64 位 Office 註冊載入項的目標平臺**

如果 MSI 包用於安裝外接程式或解決方案，則無需安裝所需的先決條件即可安裝。 如果未安裝先決條件，則可以使用 MSI 中的啟動條件來阻止外接程式安裝。

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>配置啟動條件以檢測 VSTO 運行時

1. 在**解決方案資源管理器**中，按右鍵**OfficeAddInSetup**。
2. 展開**視圖**。
3. 按一下 **"啟動條件**"。
4. 在**啟動條件（OfficeAddInSetup）編輯器中**，按右鍵**目的電腦上的"要求"，** 然後按一下"**添加登錄開機條件**"。 此搜尋條件可以在註冊表中搜索 VSTO 運行時安裝的金鑰。 然後，通過命名屬性向安裝程式的各個部分提供金鑰的值。 啟動條件使用搜尋條件定義的屬性來檢查特定值。
5. 在**啟動條件（OfficeAddInSetup）編輯器中**，選擇 **"搜索登錄機碼1"** 搜尋條件，按右鍵條件，然後選擇 **"屬性視窗**"。

6. 在 [屬性] **** 視窗中，設定這些屬性：
   1. 將 **（名稱）** 的值設置為**搜索 VSTO 2010 運行時**。
   2. 將**屬性**的值更改為**VSTORUNTIMEREDIST**。
   3. 將**RegKey**的值設置為**軟體\\微軟\\VSTO 運行時\\設置 v4R**
   4. 將**根**屬性設置為**vsdrrHKLM**。
   5. 將 **"值"** 屬性更改為**版本**。

7. 在**啟動條件（OfficeAddInSetup）編輯器中**，選擇 **"條件1**啟動條件"，按右鍵條件，然後選擇 **"屬性視窗**"。
8. 在 [屬性] 視窗中，設定這些屬性：
   1. 將 **（名稱）** 設置為**驗證 VSTO 2010 運行時可用性**。
   2. 將**條件**的值更改為**\>VSTORUNTIMEREDIST ="10.0.30319"**
   3. 將**InstallURL**屬性留空。
   4. 將 **"消息**設置為**視覺化工作室 2010"未安裝用於辦公室運行時的工具。請運行安裝程式.exe 以安裝外接程式**。

        ![驗證運行時可用性啟動條件的屬性視窗螢幕截圖](media/setup-project-figure-8.jpg)

        **圖 8：驗證運行時可用性啟動條件的屬性視窗**

 上述啟動條件顯式檢查由引導套裝程式安裝 VSTO 運行時是否存在。

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>配置啟動條件以檢測 Office 安裝的 VSTO 運行時

1. 在**啟動條件（OfficeAddInSetup）編輯器中**，按右鍵 **"搜索目的電腦**"，然後按一下"**添加註冊表搜索**"。
2. 選擇 **"搜索登錄機碼1"** 搜尋條件，按右鍵條件，然後選擇 **"屬性視窗**"。
3. 在 [屬性] **** 視窗中，設定這些屬性：
    1. 將 **（名稱）** 的值設置為**搜索 Office VSTO 運行時**。
    2. 將**屬性**的值更改為**Office Runtime**。
    3. 將**RegKey**的值設置為**軟體\\微軟\\VSTO 運行時\\設置 v4**。
    4. 將**根**屬性設置為**vsdrrHKLM**。
    5. 將 **"值"** 屬性更改為**版本**。

4. 在**啟動條件（OfficeAddInSetup）編輯器中**，選擇 **"驗證 VSTO 2010 運行時可用性**啟動條件"，按右鍵條件，然後選擇 **"屬性視窗**"。

5. 將**條件**屬性的值更改為**VSTORUNTIMEREDIST \>= "10.0.30319" 或 OFFICERUNTIME\>= "10.0.21022"。** 根據外接程式所需的執行階段版本，版本號可能會有所不同。

    ![啟動條件的屬性視窗螢幕截圖](media/setup-project-figure-9.jpg)
  
    **圖 9：通過 Redist 或 Office 啟動條件驗證運行時可用性的屬性視窗**

如果外接程式的目標是 .NET 框架 4 或更新，則可以將引用的主互通程式集 （PIA） 中的類型嵌入到 VSTO 程式集中。

要通過執行以下步驟來檢查 Interop 類型是否會嵌入到外接程式中：

1. 展開解決方案資源管理器中的參考節點
2. 選擇其中一個 PIA**引用，例如**Office 。
3. 通過點擊 F4 或從"程式集"內容功能表中選擇"屬性"來查看屬性視窗。
4. 檢查屬性**嵌入互操作類型的值**。

如果該值設置為**True，** 則嵌入類型，您可以向下跳到[**"新建設置專案**](#to-build-the-setup-project)"部分。

有關詳細資訊，請參閱[類型等效和嵌入式互操作類型](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>配置啟動條件以檢測 Office PIA 的啟動條件

1. 在**啟動條件（OfficeAddInSetup）編輯器中**，按右鍵**目的電腦上的"要求"，****然後按一下"添加 Windows 安裝程式啟動條件**"。 此啟動條件通過搜索特定元件 ID 來搜索 Office PIA。
2. 按右鍵 **"搜索元件 1"** 並按一下 **"屬性"視窗**以顯示啟動條件的屬性。
3. 在**屬性視窗中**，設置以下屬性：

    1. 將 **（名稱）** 屬性的值更改為 **"搜索辦公室共用 PIA"**
    2. 將元件**ID**的值更改為正在使用的 Office 元件的元件 ID。 您可以在下表中找到元件 ID 清單，例如 **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}。**
    3. 將**屬性**屬性的值更改為**HASSHAREDPIA**。

4. 在**啟動條件（OfficeAddInSetup）編輯器中**，按右鍵 **"條件 1"，** 然後按一下 **"屬性"視窗**以顯示啟動條件的屬性。

5. 更改**條件1**的這些屬性 ：

    1. 將 **（名稱）** 更改為**驗證辦公室共用 PIA 可用性**。
    2. 將**條件**更改為**HASSHAREDPIA**。
    3. 將**安裝 Url**留空。
    4. 將**消息**更改為**與 Excel 交互所需的元件不可用。請運行 setup.exe**。

    ![驗證辦公室共用 PIA 啟動條件的屬性視窗螢幕截圖](media/setup-project-figure-10.jpg)
  
    **圖 10：驗證辦公室共用 PIA 啟動條件的屬性視窗**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>微軟辦公室主交互程式集的元件 ID

|主交互操作程式集|Office 2010|Office 2013|辦公室 2013 （64 位）|Office 2016|辦公室 2016 （64 位）|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|[EA7564AC-C67D-4868-BE5C-26E4FC2223FF]|[C8A65ABE-3270-4FD7-B854-50C8082C8F39]|[E3BD1151-B9CA-4D45-A77E-51A6E0ED322A]|C4ACE6DB-AA99-401F-8BE6-8784BD09F003*|[C4ACE6DB-AA99-401F-8BE6-8784BD09F003]|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA]|[0F825A16-25B2-4771-A497-FC8AF3B355D8]|[C5BBD36E-B320-47EF-A512-556B99CB7E41]|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2]|[F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136]|{7824A03F-28CC-4371-BC54-93D15EFC1E7F]|[7C6D92EF-7B45-46E5-8670-819663220E4E]|[7C6D92EF-7B45-46E5-8670-819663220E4E]|
|PowerPoint|[EECBA6B8-3A62-44AD-99EB-866625466F9]|{813139AD-6DAB-4DD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|[E0A76492-0FD5-4EC2-8570-AE1BAA61DC88]|[E0A76492-0FD5-4EC2-8570-AE1BAA61DC88]|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|[C1713368-12A8-41F1-ACA1-934B01AD6EEB]|[2CC0B221-22D2-4C15-A9FB-DE818E51AF75]|{2D4540EC-2C88-4C28-AE88-2614B5460648]|{2D4540EC-2C88-4C28-AE88-2614B5460648]|
|Word|[8B74A499-37F8-4DEA-B5A0-D72FC501CEFA]|[9FE736B7-B1EE-410C-8D07-082891C3DAC8]|[13C07AF5-B206-4A48-BB5B-B8022333E3CA]|[DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161]|[DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161]|
|微軟表格 2.0|[B2279272-3FD2-434D-B94E-E4E0F8561AC4]|[B2279272-3FD2-434D-B94E-E4E0F8561AC4]|[A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC]|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510]|-|-|
|Smart Tag (智慧標籤)|{7102C98C-EF47-4F04-A227-FE33650BF954]|{487A7921-EB3A-4262-BB5B-A5736B732486}|[74EFC1F9-747D-4867-B951-EFCF29F51AF7]|-|-|
|辦公室共用|[64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4]|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E]|{76601EBB-44A7-49EE-8DE3-7B7B9D7EB05]|{625F5772-C1B3-497E-8ABE-7254EDB00506]|{625F5772-C1B3-497E-8ABE-7254EDB00506]|
|隨附此逐步解說的專案|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|[1C50E422-24FA-44A9-A120-E88280C8C341]|{706D7F44-8231-489D-9B25-3025ADE9F114]|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![最終啟動條件的螢幕截圖](media/setup-project-figure-11.jpg)

  **圖11：最終發射條件**

您可以進一步優化 ExcelAddIn 安裝的啟動條件。 例如，檢查是否安裝了實際的目標 Office 應用程式可能很有用。

### <a name="to-build-the-setup-project"></a>生成設置專案

1. 在**解決方案資源管理器**中，按右鍵**OfficeAddInSetup**專案，然後按一下 **"生成**"。
2. 使用**Windows 資源管理器**，導航到**OfficeAddInSetup**專案的輸出目錄，然後轉到"發佈"或"調試"資料夾，具體取決於所選的組建組態。 將所有檔從資料夾複製到使用者可以訪問的位置。

測試 ExcelAddIn 設置

1. 導航到將**OfficeAddInSetup**複製到的位置。
2. 按兩下 setup.exe 檔以安裝**OfficeAddInSetup**外接程式。 接受顯示的任何軟體授權條款，並完成設置嚮導以在使用者電腦上安裝外接程式。

Excel Office 解決方案應從設置期間指定的位置安裝和運行。

## <a name="additional-requirements-for-document-level-solutions"></a>文檔級解決方案的其他要求

在 Windows 安裝程式安裝程式專案中，部署文檔級解決方案需要幾個不同的配置步驟。

以下是部署文檔級解決方案所需的基本步驟的清單：

- 創建視覺化工作室設置專案。
- 添加文檔級解決方案的主要輸出。 主輸出還包括 Microsoft Office 文檔。
- 將部署和應用程式清單添加為鬆散檔。
- 從安裝套裝程式中排除從屬元件（任何實用程式程式集除外）。
- 配置必備包。
- 配置啟動條件。
- 生成設置專案並將結果複製到部署位置。
- 通過執行設置在使用者電腦上部署文檔級解決方案。
- 如果需要，更新自訂文件屬性。

### <a name="changing-the-location-of-the-deployed-document"></a>更改已部署文檔的位置

Office 文檔中的屬性用於查找文檔級別解決方案。 如果文檔安裝到與 VSTO 程式集相同的資料夾中，則無需進行任何更改。 但是，如果將其安裝到不同的資料夾，則這些屬性需要在設置期間更新。

有關這些文件屬性的詳細資訊，請參閱[自訂文件屬性概述](custom-document-properties-overview.md)。

要更改這些屬性，需要在設置期間使用自訂操作。

下面的示例使用稱為 ExcelWorkbookProject 的文檔級解決方案和稱為 ExcelWorkbook安裝程式的設置專案。 ExcelWorkbook安裝程式專案使用上述步驟進行配置，但設置登錄機碼除外。

將自訂操作專案添加到視覺化工作室解決方案

1. 通過按右鍵**解決方案資源管理器**中的**Office 文檔部署專案**，將新的 .NET 主控台專案添加到解決方案中
2. 展開 **"添加"** 並按一下 **"新專案**"。
3. 選擇主控台應用範本並命名專案 **"添加自訂自訂操作**"。

    ![解決方案資源管理器的螢幕截圖 - 添加自訂自訂操作](media/setup-project-figure-15.jpg)
  
    **圖 12：解決方案資源管理器 - 添加自訂自訂操作**

4. 添加對這些程式集的引用：
    1. System.ComponentModel
    2. System.Configuration.Install
    3. 微軟.VisualStudio.工具.應用程式
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. 將此代碼複製到Program.cs或程式.vb

```csharp
    using System;
    using System.IO;
    using System.Collections;
    using System.ComponentModel;
    using System.Configuration.Install;
    using Microsoft.VisualStudio.Tools.Applications;
    using Microsoft.VisualStudio.Tools.Applications.Runtime;

    namespace AddCustomizationCustomAction
    {
        [RunInstaller(true)]
        public class AddCustomizations : Installer
        {
            public AddCustomizations() : base() { }

            public override void Install(IDictionary savedState)
            {
                base.Install(savedState);

                //Get the CustomActionData Parameters
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;
                string assemblyLocation = Context.Parameters.ContainsKey("assemblyLocation") ? Context.Parameters["assemblyLocation"] : String.Empty;
                string deploymentManifestLocation = Context.Parameters.ContainsKey("deploymentManifestLocation") ? Context.Parameters["deploymentManifestLocation"] : String.Empty;
                Guid solutionID = Context.Parameters.ContainsKey("solutionID") ? new Guid(Context.Parameters["solutionID"]) : new Guid();

                string newDocLocation = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation));

                try
                {
                    //Move the file and set the Customizations
                    if (Uri.TryCreate(deploymentManifestLocation, UriKind.Absolute, out Uri docManifestLocationUri))
                    {
                        File.Move(documentLocation, newDocLocation);
                        ServerDocument.RemoveCustomization(newDocLocation);
                        ServerDocument.AddCustomization(newDocLocation, assemblyLocation,
                                                        solutionID, docManifestLocationUri,
                                                        true, out string[] nonpublicCachedDataMembers);
                    }
                    else
                    {
                        LogMessage("The document could not be customized.");
                    }
                }
                catch (ArgumentException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (DocumentNotCustomizedException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (InvalidOperationException)
                {
                    LogMessage("The customization could not be removed.");
                }
                catch (IOException)
                {
                    LogMessage("The document does not exist or is read-only.");
                }
            }

            public override void Rollback(IDictionary savedState)
            {
                base.Rollback(savedState);
                DeleteDocument();
            }
            public override void Uninstall(IDictionary savedState)
            {
                base.Uninstall(savedState);
                DeleteDocument();
            }
            private void DeleteDocument()
            {
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;

                try
                {
                    File.Delete(Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation)));
                }
                catch (Exception)
                {
                    LogMessage("The document doesn't exist or is read-only.");
                }
            }
            private void LogMessage(string Message)
            {
                if (Context.Parameters.ContainsKey("LogFile"))
                {
                    Context.LogMessage(Message);
                }
            }

            static void Main() { }
            }
    }
```

要將自訂添加到文檔，您需要具有 VSTO 文檔級解決方案的解決方案 ID。 此值將從視覺化工作室專案檔案中檢索。

檢索解決方案 ID

1. 在 **"生成**"功能表上，按一下 **"生成解決方案**"以生成文檔級解決方案，並將解決方案 ID 屬性添加到專案檔案中。
2. 在**解決方案資源管理器**中，按右鍵文檔級專案**ExcelWorkbook 專案**
3. 按一下 **"卸載專案"** 從視覺化工作室內部訪問專案檔案。

    ![解決方案資源管理器卸載 Excel 文檔解決方案的螢幕截圖](media/setup-project-figure-16.jpg)

    **圖 13：卸載 Excel 文檔解決方案**

4. 在**解決方案資源管理器**中，按右鍵**ExcelWorkbook 專案**，然後按一下 **"編輯ExcelWorkbookProject.vbproj"** 或 **"編輯 ExcelWorkbookProject.csproj**"。
5. 在**ExcelWorkbook 專案**編輯器中，在**屬性組**元素中找到**解決方案ID**元素。
6. 複製此元素的 GUID 值。

    ![檢索解決方案 ID](media/setup-project-figure-17.jpg)

    **圖 14：檢索解決方案 ID**

7. 在**解決方案資源管理器**中，按右鍵**ExcelWorkbook 專案**，然後按一下 **"重新載入專案**"。
8. 在對話方塊中按一下 **"是**"，該對話方塊顯示關閉**ExcelWorkbook 專案**編輯器。
9. **解決方案 ID**將在安裝自訂操作中使用。

最後一步是為**安裝**和**卸載**步驟配置自訂操作。

### <a name="to-configure-the-setup-project"></a>配置設置專案

1. 在**解決方案資源管理器**中，按右鍵**ExcelWorkbook安裝程式**，展開 **"添加"** 並按一下 **"專案輸出**"。
2. 在"**添加專案輸出組"** 對話方塊中，在 **"專案**"清單中，按一下"**添加自訂自訂操作**"。
3. 選擇 **"主輸出**"並按一下"**確定**"以關閉對話方塊，並將包含自訂操作的程式集添加到設置專案中。

    ![文檔清單自訂操作的螢幕截圖 - 添加專案輸出組視窗](media/setup-project-figure-18.jpg)

    **圖 15：文檔清單自訂操作 - 添加專案輸出組**

4. 在**解決方案資源管理器**中，按右鍵**ExcelWorkbook 安裝程式**。
5. 展開**視圖**並按一下 **"自訂操作**"。
6. 在**自訂操作（ExcelWorkbook安裝程式）** 編輯器中，按右鍵 **"自訂操作"，** 然後按一下"**添加自訂操作**"。
7. 在 **"專案中選擇專案**"對話方塊中，在"**查找"** 清單中按一下 **"應用程式資料夾**"。 **從 AddCustomCustomAction（活動）中選擇主輸出，** 然後按一下 **"確定"** 將自訂操作添加到安裝步驟。
8. 在 **"安裝"節點**下，按右鍵**AddCustomAction（活動）的主輸出**，然後按一下 **"重命名**"。 將自訂操作 **"將文檔複製到"我的文件"並附加自訂項**。
9. 在**卸載節點**下，按右鍵**AddCustomAction（活動）的主輸出**，然後按一下 **"重命名**"。 命名自訂操作**從"文檔"資料夾中刪除文檔**。

    ![文檔清單自訂操作視窗的螢幕截圖](media/setup-project-figure-19.jpg)

    **圖 16：文檔清單自訂操作**

10. 在**自訂操作 （ExcelWorkbook安裝程式）** 編輯器中，按右鍵 **"將文檔複製到"我的文件"並附加自訂項**，然後按一下"**屬性視窗**"。
11. 在 **"自訂運算元據****屬性**"視窗中，輸入自訂 DLL 的位置、部署清單和 Microsoft Office 文檔的位置。 還需要解決方案 ID。
12. 如果要將任何設置錯誤記錄到檔，請包括 LogFile 參數。
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![將文檔複製到"我的文件屬性"視窗的自訂操作的螢幕截圖](media/setup-project-figure-20.jpg)

    **圖 17：將文檔複製到我的文件的自訂操作**

13. 卸載的自訂操作需要文檔的名稱，您可以通過**在"自訂運算元據"** 中使用相同的文檔定位參數來提供

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. 編譯和部署**ExcelWorkbook 安裝程式**專案。
15. 查看 **"我的文件"** 資料夾，然後打開 ExcelWorkbookProject.xlsx 檔。

## <a name="additional-resources"></a>其他資源

[如何：安裝用於辦公室運行時的視覺化工作室工具](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Office Primary Interop Assemblies](office-primary-interop-assemblies.md)

[VSTO 外接程式的登錄機碼](registry-entries-for-vsto-add-ins.md)

[Custom Document Properties Overview](custom-document-properties-overview.md)

[在 Windows 註冊表中指定表單區域](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Granting Trust to Documents](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>關於作者

Wouter van Vugt 是 Microsoft MVP，擁有 Office 開放 XML 技術，是專注于創建具有 SharePoint、Microsoft Office 和相關 .NET 技術的 Office 商務應用程式 （OBA） 的獨立顧問。
沃特是開發商社區網站（如[OpenXmlDeveloper.org](http://openxmldeveloper.org/)和[MSDN）](/previous-versions/office/developer/office-2007/bb879915(v=office.12))的頻繁貢獻者。 他發表了幾篇白皮書和文章，以及一本線上文章，名為"打開 XML：解釋電子書"。
Wouter 是 Code-Counsel 的創始人，這家荷蘭公司專注于通過各種管道提供尖端技術內容。 你可以通過閱讀他的博客和訪問[代碼顧問網站](http://www.code-counsel.net/)來瞭解更多關於伍特的資訊。

泰德·帕蒂森是 SharePoint MVP、作者、培訓師和泰德·帕蒂森集團的創始人。 2005 年秋季，Ted 被 Microsoft 的開發人員平臺福音組聘用，為 Windows SharePoint 服務 3.0 和 Microsoft Office SharePoint Server 2007 撰寫了 Ascend 開發人員培訓課程。 從那時起，Ted 一直專注于對專業開發人員進行 SharePoint 2007 技術教育。 Ted 為 Microsoft 出版社撰寫了一本名為《Windows SharePoint 服務 3.0》的書，該書重點介紹了如何使用 SharePoint 作為構建業務解決方案的開發平臺。 Ted 還為 MSDN 雜誌撰寫了一個標題為"辦公空間"的面向開發人員的專欄。
