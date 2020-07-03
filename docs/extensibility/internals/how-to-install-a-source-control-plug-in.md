---
title: 如何：安裝原始檔控制外掛程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f88e4781115fa7a5fac54826304ab32472eeefb
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905359"
---
# <a name="how-to-install-a-source-control-plug-in"></a>如何：安裝原始檔控制外掛程式
建立原始檔控制外掛程式包含三個步驟：

1. 使用本檔的原始檔控制外掛程式 API 參考一節中所定義的函式來建立 DLL。

2. 執行原始檔控制外掛程式 API 定義的函式。 當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 呼叫它時，讓介面和對話方塊可從外掛程式取得。

3. 藉由建立適當的登錄專案來註冊 DLL。

## <a name="integration-with-visual-studio"></a>與 Visual Studio 整合
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援符合原始檔控制外掛程式 API 的原始檔控制外掛程式。

### <a name="register-the-source-control-plug-in"></a>註冊原始檔控制外掛程式
 在執行中的整合式開發環境（IDE）可以呼叫原始檔控制系統之前，它必須先找出可匯出 API 的原始檔控制外掛程式 DLL。

#### <a name="to-register-the-source-control-plug-in-dll"></a>註冊原始檔控制外掛程式 DLL

1. 在 [**軟體**] 子機碼中，新增兩個**HKEY_LOCAL_MACHINE**專案，並在其中指定您的公司名稱子機碼，後面接著您的產品名稱子機碼 模式是**HKEY_LOCAL_MACHINE \\ \<company name> \\ \<product name> \software \\ 值 \<entry> **  =  * *。 這兩個專案一律稱為**SCCServerName**和**SCCServerPath**。 每個都是一般字串。

    例如，如果您的公司名稱是 Microsoft，而您的原始檔控制產品名為 SourceSafe，則此登錄路徑會是**HKEY_LOCAL_MACHINE \software\microsoft\sourcesafe**。 在此子機碼中，第一個專案**SCCServerName**是使用者可讀取的字串，其命名為您的產品。 第二個專案**SCCServerPath**是 IDE 應連接之原始檔控制外掛程式 DLL 的完整路徑。 以下提供範例登錄專案：

   |範例登錄專案|範例值|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath 是 SourceSafe 外掛程式的完整路徑。 您的原始檔控制外掛程式將會使用不同的公司和產品名稱，但具有相同的登錄專案路徑。

2. 下列選擇性登錄專案可以用來修改原始檔控制外掛程式的行為。 這些專案會與**SccServerName**和**SccServerPath**放在相同的子機碼中。

   - 如果您不想要讓原始檔控制外掛程式出現在的**外掛程式選擇**清單中，則可以使用**HideInVisualStudioregistry**專案 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 這個專案也會影響自動切換到原始檔控制外掛程式。 如果您提供的原始檔控制封裝會取代您的原始檔控制外掛程式，但是您想要讓使用者更輕鬆地從使用原始檔控制外掛程式遷移至原始檔控制封裝，這個專案可能會有一個用途。 安裝原始檔控制套件時，它會設定這個登錄專案，這會隱藏外掛程式。

      **HideInVisualStudio**是 DWORD 值，而且會設定為*1*以隱藏外掛程式，或使用*0*來顯示外掛程式。 如果登錄專案未出現，則預設行為是顯示外掛程式。

   - **DisableSccManager**登錄專案可用來停用或隱藏通常會出現在 [檔案原始檔控制] 子功能表**底下的 [****啟動 \<Source Control Server> ** ] 功能表選項  >  **Source Control** 。 選取此功能表選項會呼叫[SccRunScc](../../extensibility/sccrunscc-function.md)函數。 您的原始檔控制外掛程式可能不支援外部程式，因此您可能會想要停用或甚至隱藏 [**啟動**] 功能表選項。

      **DisableSccManager**是 DWORD 值，設定為*0* ，可啟用 [ ** \<Source Control Server> 啟動**] 功能表選項，設定為*1*以停用功能表選項，並將設定為*2*以隱藏功能表選項。 如果未出現此登錄專案，則預設行為是顯示 [功能表] 選項。

   | 範例登錄專案 | 範例值 |
   | - |--------------|
   | HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. 在**軟體**子機碼中的**HKEY_LOCAL_MACHINE**金鑰底下，新增子機碼**SourceCodeControlProvider**。

    在此子機碼底下，登錄專案**ProviderRegKey**會設定為字串，代表您在步驟1中放置於登錄中的子機碼。 此模式為**HKEY_LOCAL_MACHINE \software\sourcecodecontrolprovider\providerregkey**  =  *SOFTWARE \\<公司名稱 \> \\<產品名稱 \> *。

    以下是此子機碼的範例內容。

   |登錄項目|範例值|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE \SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > 您的原始檔控制外掛程式會使用相同的子機碼和專案名稱，但值會不同。

4. 在**SourceCodeControlProvider**子機碼底下，建立名為**InstalledSCCProviders**的子機碼，然後在該子機碼下放置一個專案。

    此專案的名稱是提供者的使用者可讀名稱（與為 SCCServerName 專案指定的值相同），而值則是再次一次在步驟1中建立的子機碼。 此模式為**HKEY_LOCAL_MACHINE \software\sourcecodecontrolprovider\installedsccproviders \\<顯示名稱 \> **  =  *軟體 \\<公司名稱 \> \\<產品名稱 \> *。

    例如：

   |範例登錄專案|範例值|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE \SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > 可以用這種方式註冊多個原始檔控制外掛程式。 這是如何 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 尋找所有已安裝之原始檔控制外掛程式 API 的外掛程式。

## <a name="how-an-ide-locates-the-dll"></a>IDE 如何尋找 DLL
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 有兩種方式可尋找原始檔控制外掛程式 DLL：

- 尋找預設的原始檔控制外掛程式，並以無訊息模式連接。

- 尋找所有已註冊的原始檔控制外掛程式，使用者可從中選擇其中一項。

  若要以第一種方式找出 DLL，IDE 會在專案**ProviderRegKey**的 [ **HKEY_LOCAL_MACHINE \software\sourcecodecontrolprovider** ] 子機碼底下尋找。 此專案的值指向另一個子機碼。 然後，IDE 會在**HKEY_LOCAL_MACHINE**下的第二個子機碼中尋找名為**SccServerPath**的專案。 此專案的值會將 IDE 指向 DLL。

> [!NOTE]
> IDE 不會從相對路徑載入 Dll （例如， *.\NewProvider.DLL*）。 必須指定 DLL 的完整路徑（例如， *c:\Providers\NewProvider.DLL*）。 這會防止載入未經授權或模擬的外掛程式 Dll，藉此增強 IDE 的安全性。

 若要以第二種方式找出 DLL，IDE 會在所有專案的**HKEY_LOCAL_MACHINE \software\sourcecodecontrolprovider\installedsccproviders**子機碼底下尋找。 每個專案都有名稱和值。 IDE 會向使用者顯示這些名稱的清單。 當使用者選擇名稱時，IDE 會尋找指向子機碼之所選名稱的值。 IDE 會在**HKEY_LOCAL_MACHINE**下的該子機碼中尋找名為**SccServerPath**的專案。 該專案的值會將 IDE 指向正確的 DLL。

 原始檔控制外掛程式必須支援這兩種方式來尋找 DLL，因此會設定**ProviderRegKey**，並覆寫任何先前的設定。 更重要的是，它必須將自己加入至**InstalledSccProviders**清單，讓使用者可以選擇要使用的原始檔控制外掛程式。

> [!NOTE]
> 由於使用**HKEY_LOCAL_MACHINE**金鑰，因此只有一個原始檔控制外掛程式可以在指定的電腦上註冊為預設的原始檔控制外掛程式（不過， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可讓使用者判斷他們想要實際用於特定方案的原始檔控制外掛程式）。 在安裝過程中，請查看是否已設定原始檔控制外掛程式;若是如此，請詢問使用者是否要將新的原始檔控制外掛程式安裝為預設值。 在卸載期間，請勿移除**HKEY_LOCAL_MACHINE \software\sourcecodecontrolprovider**中所有原始檔控制外掛程式通用的其他登錄子機碼。只移除您特定的 SCC 子機碼。

## <a name="how-the-ide-detects-version-1213-support"></a>IDE 如何偵測 1.2/1.3 版的支援
 如何偵測 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 外掛程式是否支援原始檔控制外掛程式 API 版本1.2 和1.3 功能？ 若要宣告 advanced 功能，原始檔控制外掛程式必須執行對應的函式：

 首先， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 檢查呼叫[SccGetVersion](../../extensibility/sccgetversion-function.md)所傳回的值。 必須大於或等於1.2。

 接下來，藉 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 由檢查 `lpSccCaps` [SccInitialize](../../extensibility/sccinitialize-function.md)上的引數，判斷是否支援特定的新功能。

 如果同時符合這兩個條件，則可以呼叫1.2 和1.3 版中支援的新函數。

## <a name="see-also"></a>另請參閱
- [開始使用原始檔控制外掛程式](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
