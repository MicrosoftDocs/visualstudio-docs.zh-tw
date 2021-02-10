---
title: 使用 Windows Installer 部署 VSTO 方案
description: 瞭解如何使用 Visual Studio 安裝程式專案部署 Office (VSTO) 增益集或檔層級方案的 Microsoft Visual Studio 工具。
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 75c2d97e8cd30bb3cf5605d50e65a68513590647
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939366"
---
# <a name="deploying-a-vsto-solution-using-windows-installer"></a>使用 Windows Installer 部署 VSTO 方案

## <a name="summary"></a>摘要

瞭解如何使用 Visual Studio 安裝程式專案部署 Office (VSTO) 增益集或檔層級方案的 Microsoft Visual Studio 工具。

Wouter van Vugt，程式碼顧問

李小明 Pattison、李小明 Pattison 群組

此文章已由 Microsoft 更新，並具備原始作者的許可權。

**適用于：** Visual Studio Tools for Office、Microsoft Office Microsoft Visual Studio。

## <a name="overview"></a>概觀

您可以開發 VSTO 方案，並使用 Windows Installer 套件來部署解決方案。 本討論內容包含部署簡單 Office 增益集的步驟。

## <a name="deployment-methods"></a>部署方法

ClickOnce 可以輕鬆地用來為您的增益集和方案建立設置。 但是，它無法安裝需要系統管理許可權的增益集，例如電腦層級增益集。

您可以使用 Windows Installer 安裝需要系統管理許可權的增益集，但需要更多努力才能建立安裝程式。

如需如何使用 ClickOnce 部署 VSTO 方案的總覽，請參閱 [使用 Clickonce 部署 Office 方案](deploying-an-office-solution-by-using-clickonce.md)。

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>部署以 VSTO 執行時間為目標的 Office 方案

在安裝 Office 方案時，ClickOnce 和 Windows Installer 套件必須進行相同的基本工作。

1. 在使用者電腦上安裝必要元件。
2. 部署解決方案的特定元件。
3. 若為增益集，請建立登錄專案。
4. 信任解決方案，讓它能夠執行。

### <a name="required-prerequisite-components-on-the-target-computer"></a>目的電腦上所需的必要元件

以下是要執行 VSTO 解決方案的電腦上必須安裝的軟體清單：

- Microsoft Office 2010 或更新版本。
- Microsoft .NET Framework 4 或更新版本。
- Microsoft Visual Studio 2010 Tools for Office Runtime。
  執行時間會提供管理增益集和檔層級方案的環境。 Microsoft Office 隨附的執行階段版本，但您可能會想要使用您的增益集來轉散發特定版本。
- 如果您不是使用內嵌的 Interop 類型，Microsoft Office 的主要 Interop 元件。
- 專案所參考的任何公用程式元件。

### <a name="specific-components-for-the-solution"></a>解決方案的特定元件

安裝程式套件必須將這些元件安裝到使用者的電腦上：

- 如果您建立檔層級方案，則 Microsoft Office 檔。
- 自訂群組件及其所需的任何元件。
- 其他元件（例如設定檔）。
- 應用程式資訊清單 ( .manifest) 。
- 部署資訊清單 ( vsto) 。

### <a name="registry-entries-for-add-ins"></a>增益集的登錄專案

Microsoft Office 使用登錄專案來找出並載入增益集。這些登錄專案應該在部署過程中建立。 如需這些登錄專案的詳細資訊，請參閱 [VSTO 增益集的登錄專案](registry-entries-for-vsto-add-ins.md)。

顯示自訂表單區域的 Outlook 增益集需要額外的登錄專案，以允許識別表單區域。 如需登錄專案的詳細資訊，請參閱 [Outlook 表單區域的登錄專案](registry-entries-for-vsto-add-ins.md#OutlookEntries)。

檔層級解決方案不需要任何登錄專案。 相反地，檔內的屬性會用來尋找自訂專案。 如需這些屬性的詳細資訊，請參閱 [自訂文件屬性總覽](custom-document-properties-overview.md)。

### <a name="trusting-the-vsto-solution"></a>信任 VSTO 方案

為了讓自訂執行，解決方案必須受機器信任。 您可以使用憑證簽署資訊清單、建立與內含清單的信任關係，或將它安裝到電腦上的受信任位置，以信任此增益集。

如需如何取得憑證以進行簽署的詳細資訊，請參閱 [ClickOnce 部署和 Authenticode](../deployment/clickonce-and-authenticode.md)。 如需信任解決方案的詳細資訊，請參閱 [使用包含清單來信任 Office 方案](trusting-office-solutions-by-using-inclusion-lists.md)。 您可以在 Windows Installer 檔案中加入包含自訂動作的內含清單專案。 如需有關啟用包含清單的詳細資訊，請參閱 how [to：設定內含清單安全性](how-to-configure-inclusion-list-security.md)。

如果未使用任何選項，則會向使用者顯示信任提示，讓他們決定是否信任方案。

如需檔層級方案相關安全性的詳細資訊，請參閱授 [與信任給檔](granting-trust-to-documents.md)。

## <a name="creating-a-basic-installer"></a>建立基本安裝程式

安裝和部署專案範本隨附于可供下載的 [Microsoft Visual Studio 安裝程式專案](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) 延伸模組。

若要建立 Office 方案的安裝程式，您必須完成下列工作：

- 新增要部署的 Office 方案元件。
- 若為應用層級增益集，請設定登錄機碼。
- 設定必要條件元件，以便在使用者電腦上安裝這些元件。
- 設定啟動條件，以確認所需的必要條件元件可用。 如果未安裝所有必要的必要條件，則可以使用啟動條件來封鎖安裝。

第一個步驟是建立安裝專案。

### <a name="to-create-the-addin-setup-project"></a>若要建立增益集安裝專案

1. 開啟您要部署的 Office 增益集專案。 在此範例中，我們使用名為 ExcelAddIn 的 Excel 增益集。
2. 開啟 Office 專案後，在 [檔案 **] 功能表上** ，展開 [ **加入** ]，然後按一下 [ **新增專案** ] 以新增專案。
::: moniker range="=vs-2017"
3. 在 [**加入新專案**] 對話方塊中，展開 **[專案類型**] 窗格中的 [**其他專案類型**]，然後展開 [**安裝和部署**]，然後選取 [ **Visual Studio 安裝程式**]。
4. 在 [**範本**] 窗格中，從 [ **Visual Studio 安裝** 的範本] 群組中選取 [**安裝專案**]。
::: moniker-end
::: moniker range="=vs-2019"
3. 在 [ **加入新專案** ] 對話方塊中，選取 [ **安裝專案** ] 範本。
4. 按一下 [下一步] 。
::: moniker-end

5. 在 [ **名稱** ] 方塊中，輸入 **officeaddinsetup]**。
::: moniker range="=vs-2017"
6. 按一下 [ **開啟** ] 以建立新的安裝專案。
::: moniker-end
::: moniker range="=vs-2019"
6. 按一下 [ **建立** ] 以建立新的安裝專案。
::: moniker-end

Visual Studio 開啟新安裝專案的檔案系統 Explorer。 檔案系統 Explorer 可讓您將檔案新增至安裝專案。

   ![安裝專案的檔案系統 Explorer 螢幕擷取畫面](media/setup-project-figure-1.png)

   **圖1：安裝專案的檔案系統 Explorer**

安裝專案需要部署 ExcelAddIn。 您可以藉由將 ExcelAddIn 專案輸出加入至安裝專案，來設定這項工作的安裝專案。

### <a name="to-add-the-exceladdin-project-output"></a>若要加入 ExcelAddIn 專案輸出

1. 在 [ **方案總管** 中，以滑鼠右鍵按一下 [ **officeaddinsetup]**]，按一下 [ **新增** ]，然後按一下 [ **專案輸出**]。
2. 在 [ **加入專案輸出群組** ] 對話方塊中，從 [專案] 清單中選取 [ **ExcelAddIn** ]，然後選取 [ **主要輸出**]。
3. 按一下 **[確定]** ，將專案輸出加入至安裝專案。

    ![[設定專案加入專案輸出群組] 對話方塊的螢幕擷取畫面](media/setup-project-figure-2.png)

    **圖2：安裝程式專案 [加入專案輸出群組] 對話方塊**

安裝專案需要部署部署資訊清單和應用程式資訊清單。 將這兩個檔案新增至安裝專案，做為 ExcelAddIn 專案輸出檔案夾中的獨立檔案。

### <a name="to-add-the-deployment-and-application-manifests"></a>加入部署和應用程式資訊清單

1. 在 [**方案總管** 中，以滑鼠右鍵按一下 [ **officeaddinsetup]**] **，按一下 [****新增**]，然後按一下 [檔案]。
2. 在 [ **新增** 檔案] 對話方塊中，流覽至 **ExcelAddIn** 輸出目錄。 輸出目錄通常是專案根目錄的 **bin \\ 發行** 子資料夾（視選取的組建設定而定）。
3. 選取ExcelAddIn.dll **ExcelAddIn** ，然後按一下 [**開啟**]，將這兩個檔案加入至安裝專案。

    ![方案總管中的應用程式和部署資訊清單的螢幕擷取畫面](media/setup-project-figure-3.jpg)

    **圖3：方案總管中增益集的應用程式和部署資訊清單**

參考 ExcelAddIn 包含 ExcelAddIn 所需的所有元件。 您必須使用必要條件套件來排除和部署這些元件，才能正確註冊這些元件。 此外，在開始安裝之前，必須先顯示並接受軟體授權條款。

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>排除 ExcelAddIn 專案相依性

1. 在 [**方案總管** **]** 的 [ **officeaddinsetup]** ] 節點中，選取 [偵測到的相依性專案] 下的 [所有相依性專案]，但 **Microsoft .NET Framework** 或任何以 **\*.Utilities.dll** 結尾的元件除外。 公用程式元件可與您的應用程式一起部署。
2. 以滑鼠右鍵按一下群組，然後選取 [ **屬性**]。
3. 在 [ **屬性** ] 視窗中，將 [ **排除** ] 屬性變更為 [ **True** ]，將相依元件從安裝專案中排除。 請務必不要排除任何公用程式元件。

    ![顯示要排除之相依性方案總管的螢幕擷取畫面](media/setup-project-figure-4.jpg)

    **圖4：排除相關性**

您可以藉由新增安裝程式（也稱為啟動載入器），設定 Windows Installer 套件來安裝必要條件元件。 此安裝程式可以安裝必要條件元件，這是一個稱為「啟動載入」的進程。

針對 **ExcelAddIn**，必須先安裝這些必要條件，增益集才能正確執行：

- Office 方案的目標 Microsoft .NET Framework 版本。
- Microsoft Visual Studio 2010 Tools for Office 執行階段。

將相依元件設定為必要條件

1. 在 [ **方案總管** 中，以滑鼠右鍵按一下 **officeaddinsetup]** 專案，然後選取 [ **屬性**]。
2. [ **Officeaddinsetup] 屬性頁** ] 對話方塊隨即出現。
3. 按一下 [ **必要條件** ] 按鈕。
4. 在 [必要條件] 對話方塊中，選取正確的 .NET Framework 版本和 Microsoft Visual Studio Tools for Office Runtime。

    ![[必要條件] 對話方塊的螢幕擷取畫面](media/setup-project-figure-5.png)

    **圖5：必要條件對話方塊**

    > [!NOTE]
    >Visual Studio 安裝專案中設定的部分必要條件套件相依于所選的組建設定。 您必須針對所使用的每個組建設定，選取正確的必要條件元件。

Microsoft Office 使用登錄機碼來尋找增益集。 HKEY \_ CURRENT user hive 中的金鑰 \_ 是用來註冊每個個別使用者的增益集。 HKEY \_ 本機電腦 hive 下的金鑰 \_ 是用來為電腦的所有使用者註冊增益集。 如需登錄機碼的詳細資訊，請參閱 [VSTO 增益集的登錄專案](registry-entries-for-vsto-add-ins.md)。

### <a name="to-configure-the-registry"></a>設定登錄

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **officeaddinsetup]**]。
2. 展開 [ **View**]。
3. 按一下 [登錄] 以開啟 **[登錄編輯程式** ] 視窗。
4. 在登錄 **(officeaddinsetup])** 編輯器] 中，依序展開 [ **HKEY \_ 本機 \_ 電腦** ] 和 [ **軟體**]。
5. 刪除在 [ **HKEY \_ 本機 \_ 電腦 \\ 軟體**] 下找到的 **\[ 製造商 \]**。
6. 展開 [ **HKEY \_ 目前 \_ 使用者** ]，然後依序展開 [ **軟體**]。
7. 刪除在 [ **HKEY \_ 目前的 \_ 使用者 \\ 軟體**] 下找到的 **\[ 製造商 \]** 金鑰。
8. 若要新增增益集安裝的登錄機碼，請以滑鼠右鍵按一下 **使用者/電腦 Hive** 機碼，然後選取 [ **新增金鑰**]。 使用文字 **軟體** 作為新金鑰的名稱。 以滑鼠右鍵按一下新建立的 **軟體** 金鑰，並使用 **Microsoft** 文字建立新的金鑰。
9. 使用類似的程式來建立增益集註冊所需的整個金鑰階層：

    **使用者/電腦 Hive \\ 軟體 \\ Microsoft \\ Office \\ Excel \\ 增益集 \\ samplecompany.exceladdin 機碼. ExcelAddIn**

    公司名稱通常用來做為增益集名稱的前置詞，以提供唯一性。

10. 以滑鼠右鍵按一下 [ **samplecompany.exceladdin 機碼. ExcelAddIn** ] 鍵，選取 [ **新增**]，然後按一下 [ **字串值**]。 使用名稱的文字 **描述** 。
11. 您可以使用此步驟來新增其他三個值：
    - **字串** 類型的 **FriendlyName**
    - **DWORD** 類型的 **LoadBehavior**
    - **字串** 類型的 **資訊清單**

12. 以滑鼠右鍵按一下登錄編輯程式中的 **描述** 值，然後按一下 [ **屬性視窗]**。 在 [ **屬性] 視窗** 中，針對 [值] 屬性輸入 **Excel 示範載入** 宏。
13. 在登錄編輯程式中，選取 [ **FriendlyName** ] 機碼。 在 [ **屬性] 視窗** 中，將 [ **值** ] 屬性變更為 **Excel 示範載入** 宏。
14. 在 [登錄編輯程式] 中選取 **LoadBehavior** 機碼。 在 [ **屬性] 視窗** 中，將 [ **值** ] 屬性變更為 **3。** LoadBehavior 的值3表示增益集應該在主應用程式啟動時載入。 如需載入行為的詳細資訊，請參閱 [VSTO 增益集的登錄專案](registry-entries-for-vsto-add-ins.md)。

15. 在 [登錄編輯程式] 中選取 **資訊清單** 索引鍵。 在 [ **屬性] 視窗** 中，將 [ **值** ] 屬性變更為 **file：///[TARGETDIR] ExcelAddIn vsto | vstolocal**

    ![登錄編輯程式的螢幕擷取畫面](media/setup-project-figure-6.png)

    **圖6：設定登錄機碼**

      VSTO 執行時間會使用這個登錄機碼來尋找部署資訊清單。 [TARGETDIR] 宏將會取代為安裝增益集的資料夾。 宏會包含尾端的 \ 字元，因此部署資訊清單的檔案名應該是 ExcelAddIn，不含 \ 字元。
      **Vstolocal** 後置詞會告知 VSTO 執行時間，增益集應該從這個位置載入，而不是 ClickOnce 快取。 移除此後置，會導致執行時間將自訂複製到 ClickOnce 快取中。

   >[!WARNING]
   >在 Visual Studio 中，您應該非常小心使用登錄編輯程式。 例如，如果您不小心針對錯誤的機碼設定 DeleteAtUninstall，您可能會刪除登錄中的使用中部分，讓使用者電腦處於不一致或更糟的狀態。

64位版本的 Office 將使用64位的登錄 hive 來尋找增益集。若要在64位登錄 hive 下登錄增益集，安裝專案的目標平臺必須設定為僅限64位。

1. 在 [方案瀏覽器] 中選取 **officeaddinsetup]** 專案。
2. 移至 [ **屬性** ] 視窗，並將 [ **TargetPlatform** ] 屬性設定為 [ **x64**]。

您必須建立兩個不同的 MSI 套件，才能同時安裝32位和64位版 Office 的增益集。 一個用於32位，另一個用於64位。

  ![[屬性] 視窗的螢幕擷取畫面，其中顯示使用64位 Office 註冊增益集的目標平臺](media/setup-project-figure-7.jpg)

  **圖7：使用64位 Office 註冊增益集的目標平臺**

如果 MSI 套件是用來安裝增益集或解決方案，則可能會在未安裝必要必要條件的情況下進行安裝。 如果未安裝必要條件，您可以使用 MSI 中的啟動條件來封鎖增益集的安裝。

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>設定啟動條件以偵測 VSTO 執行時間

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **officeaddinsetup]**]。
2. 展開 [ **View**]。
3. 按一下 [ **啟動條件**]。
4. 在 [ **啟動條件 (officeaddinsetup])** 編輯器] 中，以滑鼠右鍵按一下 [ **目的電腦上的需求**]，然後按一下 [ **新增登錄啟動條件**]。 此搜尋條件可以在登錄中搜尋 VSTO 執行時間所安裝的金鑰。 然後，您可以透過已命名的屬性，將金鑰的值提供給安裝程式的各個部分。 啟動條件會使用搜尋條件所定義的屬性來檢查某個值。
5. 在 [ **啟動條件 (officeaddinsetup])** 編輯器] 中，選取 [ **搜尋 RegistryEntry1** 搜尋條件]，以滑鼠右鍵按一下條件，然後選取 [ **屬性視窗]**。

6. 在 [屬性]  視窗中，設定這些屬性：
   1. 將 **(名稱)** 的值設定為 **搜尋 VSTO 2010 運行** 時間。
   2. 將 **屬性** 的值變更為 **VSTORUNTIMEREDIST**。
   3. 將 [ **RegKey** ] 的值設定為 [ **SOFTWARE \\ Microsoft \\ VSTO Runtime 安裝 \\ v4R** ]
   4. 將 [ **根** ] 屬性設定為 [ **vsdrrHKLM**]。
   5. 將 [ **值** ] 屬性變更為 [ **版本**]。

7. 在 [ **啟動條件 (officeaddinsetup])** 編輯器] 中，選取 [ **Condition1** 啟動條件]，以滑鼠右鍵按一下條件，然後選取 [ **屬性視窗]**。
8. 在 [屬性] 視窗中，設定這些屬性：
   1. 設定 **(名稱)** 以 **驗證 VSTO 2010 執行時間可用性**。
   2. 將 **條件** 的值變更為 **VSTORUNTIMEREDIST \> = "10.0.30319"**
   3. 將 **InstallURL** 屬性保留空白。
   4. 將 **訊息** 設定為 **未安裝適用于 Office Runtime 的 Visual Studio 2010 工具。請執行 Setup.exe 來安裝增益集**。

        ![[驗證執行時間可用性] 啟動條件之 [屬性] 視窗的螢幕擷取畫面](media/setup-project-figure-8.jpg)

        **圖8： [驗證執行時間可用性] 啟動條件的 [屬性] 視窗**

 上述啟動條件會在啟動載入器套件安裝時，明確檢查 VSTO 執行時間是否存在。

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>設定啟動條件以偵測 Office 所安裝的 VSTO 執行時間

1. 在 [ **啟動條件] (officeaddinsetup])** 編輯器] 中，以滑鼠右鍵按一下 [ **搜尋目的電腦**]，然後按一下 [ **新增登錄搜尋**]。
2. 選取 [ **搜尋 RegistryEntry1** 搜尋條件]，以滑鼠右鍵按一下條件，然後選取 [ **屬性視窗]**。
3. 在 [屬性]  視窗中，設定這些屬性：
    1. 將 **(名稱)** 的值設定為 **搜尋 Office VSTO Runtime**。
    2. 將 **屬性** 的值變更為 **OfficeRuntime**。
    3. 將 [ **RegKey** ] 的值設定為 [ **SOFTWARE \\ Microsoft \\ VSTO Runtime Setup \\ v4**]。
    4. 將 [ **根** ] 屬性設定為 [ **vsdrrHKLM**]。
    5. 將 [ **值** ] 屬性變更為 [ **版本**]。

4. 在 [ **啟動條件 (officeaddinsetup])** 編輯器] 中，選取 [驗證之前定義的 **VSTO 2010 執行時間可用性** 啟動條件]，以滑鼠右鍵按一下條件，然後選取 [ **屬性視窗]**。

5. 將 **Condition** 屬性的值變更為 **VSTORUNTIMEREDIST \> = "10.0.30319" 或 OFFICERUNTIME \> = "10.0.21022"**。 根據您的增益集所需的執行階段版本，版本號碼可能會不同。

    ![啟動條件之 [屬性] 視窗的螢幕擷取畫面](media/setup-project-figure-9.jpg)
  
    **圖9：透過可轉散發套件或 Office 啟動條件驗證執行時間可用性的屬性視窗**

如果增益集以 .NET Framework 4 或更新版本為目標，則會將所參考之主要 Interop 元件中的類型 (PIA) ）內嵌至 VSTO 元件中。

若要檢查 Interop 類型是否會在增益集中內嵌，請執行下列步驟：

1. 展開方案總管中的 [參考] 節點
2. 選取其中一個 PIA 參考，例如 **Office**。
3. 藉由叫用 F4 或從元件內容功能表中選取 [屬性]，來查看 [屬性] 視窗。
4. 檢查 [ **內嵌 Interop 類型**] 屬性的值。

如果值設定為 **True**，則會內嵌型別，您可以跳到 [**以建立安裝專案**](#to-build-the-setup-project) 區段。

如需詳細資訊，請參閱 [類型等價和內嵌 Interop 類型](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>若要設定啟動條件以偵測 Office Pia 的情況

1. 在 [ **啟動條件] (officeaddinsetup])** 編輯器] 中，以滑鼠右鍵按一下 [ **目的電腦上的需求**]，然後 **按一下 [新增] Windows Installer 啟動條件**。 此啟動條件會搜尋特定的元件識別碼，以搜尋 Office PIA。
2. 以滑鼠右鍵按一下 [ **搜尋 Component1** ]，然後按一下 [ **屬性視窗]** 來顯示啟動條件的屬性。
3. 在 [ **屬性] 視窗** 中，設定下列屬性：

    1. 將 **(名稱)** 屬性的值變更為 **搜尋 Office 共用 PIA**
    2. 將 [元件識別碼] 的值 **變更為您** 要使用之 Office 元件的元件識別碼。 您可以在下表中找到元件識別碼的清單，例如 **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**。
    3. 將 [ **屬性** ] 屬性的值變更為 **HASSHAREDPIA**。

4. 在 [ **啟動條件 (officeaddinsetup])** 編輯器] 中，以滑鼠右鍵按一下 [ **Condition1** ]，然後按一下 [ **屬性視窗]** 來顯示啟動條件的屬性。

5. 變更 **Condition1** 的下列屬性：

    1. 變更 **(名稱)** 以 **確認 Office 共用 PIA 的可用性**。
    2. 將 **條件** 變更為 **HASSHAREDPIA**。
    3. 將 **InstallUrl** 保留空白。
    4. 將 **訊息** 變更為 **無法與 Excel 互動的必要元件。請 setup.exe執行**。

    ![確認 Office 共用 PIA 啟動條件之 [屬性] 視窗的螢幕擷取畫面](media/setup-project-figure-10.jpg)
  
    **圖10：驗證 Office 共用 PIA 啟動條件的 [屬性] 視窗**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>Microsoft Office 之主要 Interop 元件的元件識別碼

|主要 interop 元件|Office 2010|Office 2013|Office 2013 (64 位) |Office 2016|Office 2016 (64 位) |
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B8022333E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2。0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Smart Tag (智慧標籤)|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Office 共用|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Project|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![最後啟動狀況的螢幕擷取畫面](media/setup-project-figure-11.jpg)

  **圖11：最終啟動條件**

您可以進一步精簡 ExcelAddIn 安裝的啟動條件。 比方說，檢查實際的目標 Office 應用程式是否已安裝，可能會很有用。

### <a name="to-build-the-setup-project"></a>若要建立安裝專案

1. 在 [ **方案總管** 中，以滑鼠右鍵按一下 **officeaddinsetup]** 專案，然後按一下 [ **建立**]。
2. 使用 **Windows 檔案總管**，流覽至 **officeaddinsetup]** 專案的輸出目錄，並移至 [發行] 或 [Debug] 資料夾（視選取的組建設定而定）。 將資料夾中的所有檔案複製到使用者可以存取的位置。

測試 ExcelAddIn 設定

1. 流覽至您將 **officeaddinsetup]** 複製到其中的位置。
2. 按兩下 setup.exe 檔案，以安裝 **officeaddinsetup]** 增益集。 接受任何出現的軟體授權條款，然後完成安裝程式以在使用者電腦上安裝增益集。

Excel Office 方案應該在安裝期間指定的位置安裝並執行。

## <a name="additional-requirements-for-document-level-solutions"></a>檔層級方案的其他需求

部署檔層級解決方案需要 Windows Installer 安裝專案中有幾個不同的設定步驟。

以下是部署檔層級解決方案所需的基本步驟清單：

- 建立 Visual Studio 安裝專案。
- 加入檔層級方案的主要輸出。 主要輸出也包含 Microsoft Office 檔。
- 將部署和應用程式資訊清單新增為鬆散式檔案。
- 除了) 的任何公用程式元件之外，請從安裝程式套件中排除相依元件 (。
- 設定必要條件套件。
- 設定啟動條件。
- 建立安裝專案，並將結果複製到部署位置。
- 執行安裝程式，在使用者電腦上部署檔層級方案。
- 視需要更新自訂文件屬性。

### <a name="changing-the-location-of-the-deployed-document"></a>變更已部署檔的位置

Office 檔內的屬性可用來尋找檔層級方案。 如果檔與 VSTO 元件安裝在相同的資料夾中，則不需要進行任何變更。 但是，如果它安裝在不同的資料夾中，則在安裝期間將需要更新這些屬性。

如需這些文件屬性的詳細資訊，請參閱 [自訂文件屬性總覽](custom-document-properties-overview.md)。

若要變更這些屬性，您必須在安裝期間使用自訂動作。

下列範例會使用名為 ExcelWorkbookProject 的檔層級方案，以及名為 ExcelWorkbookSetup 的安裝專案。 ExcelWorkbookSetup 專案是使用上面所述的相同步驟來設定，但設定登錄機碼除外。

將自訂動作專案新增至您的 Visual Studio 方案

1. 以滑鼠右鍵按一下 **方案總管** 中的 **Office 檔部署專案**，以將新的 .net 主控台專案加入方案中
2. 展開 [ **加入** ]，然後按一下 [ **新增專案**]。
3. 選取 [主控台應用程式] 範本，並將專案命名為 **AddCustomizationCustomAction**。

    ![方案總管-AddCustomizationCustomAction 的螢幕擷取畫面](media/setup-project-figure-15.jpg)
  
    **圖12：方案總管-AddCustomizationCustomAction**

4. 新增這些元件的參考：
    1. System.ComponentModel
    2. System.Configuration.Install
    3. VisualStudio 應用程式
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. 將此程式碼複製到 Program.cs 或 .vb

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

若要將自訂新增至檔，您必須擁有 VSTO 檔層級方案的方案識別碼。 此值會從 Visual Studio 的專案檔中取出。

若要取得解決方案識別碼

1. 在 [ **組建** ] 功能表上，按一下 [ **建立方案** ] 來建立檔層級方案，並將 [方案識別碼] 屬性加入至專案檔。
2. 在 **方案總管** 中，以滑鼠右鍵按一下檔層級專案 **ExcelWorkbookProject**
3. 按一下 [ **UnloadProject** ] 以從 Visual Studio 記憶體取專案檔。

    ![卸載 Excel 檔方案方案總管的螢幕擷取畫面](media/setup-project-figure-16.jpg)

    **圖13：卸載 Excel 檔方案**

4. 在 **方案總管** 中，以滑鼠右鍵按一下 **ExcelWorkbookProject** ，然後按一下 [EditExcelWorkbookProject]，再按一下 [ **Vbproj** ] 或 [ **編輯 ExcelWorkbookProject**]。
5. 在 [ **ExcelWorkbookProject** 編輯器] 中，找出 **PropertyGroup** 元素內的 **SolutionID** 元素。
6. 複製此元素的 GUID 值。

    ![正在抓取 SolutionID](media/setup-project-figure-17.jpg)

    **圖14：正在抓取 SolutionID**

7. 在 **方案總管** 中，以滑鼠右鍵按一下 **ExcelWorkbookProject** ，然後按一下 [ **重載專案**]。
8. 在出現的對話方塊中按一下 [ **是** ]，以關閉 [ **ExcelWorkbookProject** 編輯器]。
9. **解決方案識別碼** 將用於安裝自訂動作。

最後一個步驟是設定 **安裝** 和 **卸載** 步驟的自訂動作。

### <a name="to-configure-the-setup-project"></a>設定安裝專案

1. 在 [ **方案總管** 中，以滑鼠右鍵按一下 [ **ExcelWorkbookSetup**]，展開 [ **加入** ]，然後按一下 [ **專案輸出**]。
2. 在 [ **加入專案輸出群組** ] 對話方塊的 [ **專案** ] 清單中，按一下 [ **AddCustomizationCustomAction**]。
3. 選取 [ **主要輸出** ]，然後按一下 **[確定** ] 關閉對話方塊，並將包含自訂動作的元件加入至安裝專案。

    ![檔資訊清單自訂動作-新增專案輸出群組視窗的螢幕擷取畫面](media/setup-project-figure-18.jpg)

    **圖15：檔資訊清單自訂動作-新增專案輸出群組**

4. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **ExcelWorkbookSetup**]。
5. 展開 [ **View** ]，然後按一下 [ **自訂動作**]。
6. 在 [**自訂動作 (ExcelWorkbookSetup)** 編輯器] 中，以滑鼠右鍵按一下 [**自訂動作**]，然後按一下 [**新增自訂動作**
7. 在 [ **在專案中選取專案** ] 對話方塊的 [ **查詢** ] 清單中，按一下 [ **應用程式資料夾**]。 **從 AddCustomizationCustomAction (active) 選取 [主要輸出**]，然後按一下 **[確定]** ，將自訂動作新增至安裝步驟。
8. 在 [ **安裝] 節點** 下，以滑鼠右鍵按一下 **AddCustomizationCustomAction (Active) 的 [主要輸出**]，然後按一下 [ **重新命名**]。 將自訂動作 **複製檔命名為我的檔並附加自訂**。
9. 在 [ **卸載] 節點** 下，以滑鼠右鍵按一下 **AddCustomizationCustomAction (Active) 的 [主要輸出** ]，然後按一下 [ **重新命名**]。 將自訂動作 **從 [檔] 資料夾** 命名為 [移除檔]。

    ![檔資訊清單自訂動作視窗的螢幕擷取畫面](media/setup-project-figure-19.jpg)

    **圖16：檔資訊清單自訂動作**

10. 在 [ **自訂動作] (ExcelWorkbookSetup)** 編輯器] 中，以滑鼠右鍵按一下 [ **複製檔]，我的檔並附加自訂** ，然後按一下 [ **屬性視窗]**。
11. 在 [ **CustomActionData** **屬性** ] 視窗中，輸入自訂 DLL 的位置、部署資訊清單，以及 Microsoft Office 檔的位置。 也需要 SolutionID。
12. 如果您想要將任何安裝錯誤記錄到檔案中，請包含 LogFile 參數。
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![將檔案複製到我的檔屬性視窗之自訂動作的螢幕擷取畫面](media/setup-project-figure-20.jpg)

    **圖17：將檔案複製到我的檔的自訂動作**

13. 卸載的自訂動作需要檔的名稱，您可以在 **CustomActionData** 中使用相同的 documentLocation 參數來提供此名稱。

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. 編譯和部署 **ExcelWorkbookSetup** 專案。
15. 查看 **我的檔** 資料夾，然後開啟 ExcelWorkbookProject.xlsx 檔案。

## <a name="additional-resources"></a>其他資源

[如何：安裝 Visual Studio Tools for Office 執行時間](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Office Primary Interop Assemblies](office-primary-interop-assemblies.md)

[VSTO 增益集的登錄專案](registry-entries-for-vsto-add-ins.md)

[Custom Document Properties Overview](custom-document-properties-overview.md)

[在 Windows 登錄中指定表單區域](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Granting Trust to Documents](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>關於作者

Wouter van Vugt 是 Office Open XML 技術的 Microsoft MVP，也是一位獨立顧問，著重于使用 SharePoint、Microsoft Office 和相關的 .NET 技術來建立 Office Business Applications (Oba) 。
Wouter 是開發人員社區網站（如 [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12))）的常見參與者。 他發表了幾篇白皮書和文章，以及一本書《 Open XML：說明的電子書》一書。
Wouter 是程式碼顧問的創辦人，這是一家荷蘭公司，致力於透過各種管道傳遞最新的技術內容。 您可以閱讀他的 blog，瞭解更多有關 Wouter 的資訊。

李小明 Pattison 是 SharePoint MVP、作者、訓練員和李小明 Pattison Group 的創辦人。 在2005秋季，李小明是由 Microsoft 的開發人員平臺推廣團隊雇用，以撰寫適用于 Windows SharePoint Services 3.0 和 Microsoft Office SharePoint Server 2007 的遞增開發人員訓練課程。 從那時起，李小明一直致力於教育專業開發人員的 SharePoint 2007 技術。 在 Windows SharePoint Services 3.0 中，李小明已完成撰寫一本書的書籍，著重于如何使用 SharePoint 做為開發平臺，以建立商務解決方案。 李小明也為 MSDN 雜誌的 MSDN 雜誌撰寫了以開發人員為主的資料行。
