---
title: 如何：安裝原始檔控制外掛程式 |Microsoft Docs
description: 瞭解如何在 Visual Studio 中安裝原始檔控制外掛程式，方法是將它與 Visual Studio 的原始檔控制外掛程式 API 整合，並註冊其 DLL。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4a0798cb7763ff2766d2de2bb00a80759be8fd3e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078808"
---
# <a name="how-to-install-a-source-control-plug-in"></a>如何：安裝原始檔控制外掛程式
建立原始檔控制外掛程式包含三個步驟：

1. 使用本檔的原始檔控制外掛程式 API 參考一節中所定義的函式來建立 DLL。

2. 執行原始檔控制外掛程式 API 定義函數。 當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 呼叫它時，請讓介面和對話方塊可從外掛程式取得。

3. 藉由建立適當的登錄專案來註冊 DLL。

## <a name="integration-with-visual-studio"></a>與 Visual Studio 整合
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援符合原始檔控制外掛程式 API 的原始檔控制外掛程式。

### <a name="register-the-source-control-plug-in"></a>註冊原始檔控制外掛程式
 在執行整合式開發環境之前 (IDE) 可以呼叫原始檔控制系統，它必須先找出可匯出 API 的原始檔控制外掛程式 DLL。

#### <a name="to-register-the-source-control-plug-in-dll"></a>註冊原始檔控制外掛程式 DLL

1. 在 **軟體** 子機碼中，于指定您公司名稱子機碼下的 **HKEY_LOCAL_MACHINE** 機碼下新增兩個專案，後面接著您的產品名稱子機碼 此模式為 **\\ \<company name> \\ \<product name>HKEY_LOCAL_MACHINE\SOFTWARE\\ 值 \<entry>**  =  **。 這兩個專案一律稱為 **SCCServerName** 和 **SCCServerPath**。 每個都是一般字串。

    例如，如果您的公司名稱是 Microsoft，而且您的原始檔控制產品名為 SourceSafe，則會 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe** 這個登錄路徑。 在這個子機碼中，第一個專案 **SCCServerName** 是使用者可讀取的字串，可為您的產品命名。 第二個專案 **SCCServerPath** 是 IDE 應該連接的原始檔控制外掛程式 DLL 的完整路徑。 以下提供範例登錄專案：

   |範例登錄專案|範例值|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath 是 SourceSafe 外掛程式的完整路徑。 您的原始檔控制外掛程式將會使用不同的公司和產品名稱，但會使用相同的登錄專案路徑。

2. 下列選擇性的登錄專案可以用來修改原始檔控制外掛程式的行為。 這些專案會進入與 **SccServerName** 和 **SccServerPath** 相同的子機碼。

   - 如果您不想讓原始檔控制外掛程式出現在的 **外掛程式選擇** 清單中，可以使用 **HideInVisualStudioregistry** 專案 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 這個專案也會影響自動切換至原始檔控制外掛程式。 如果您提供原始檔控制套件來取代您的原始檔控制外掛程式，但您想要讓使用者更輕鬆地使用原始檔控制封裝將原始檔控制外掛程式遷移至原始檔控制封裝，則可以使用此專案。 安裝原始檔控制封裝時，它會設定這個登錄專案，這會隱藏外掛程式。

      **HideInVisualStudio** 是 DWORD 值，且設定為 *1* 以隱藏外掛程式或 *0* 以顯示外掛程式。 如果登錄專案未出現，則預設行為是顯示外掛程式。

   - **DisableSccManager** 登錄專案可以用來停用或隱藏通常會出現在 [檔案原始檔控制] 子功能表 **底下的 [****啟動 \<Source Control Server>** ] 功能表選項  >   。 選取此功能表選項會呼叫 [SccRunScc](../../extensibility/sccrunscc-function.md) 函數。 您的原始檔控制外掛程式可能不支援外部程式，因此您可能會想要停用或甚至隱藏 [ **啟動** ] 功能表選項。

      **DisableSccManager** 是一個 DWORD 值，且設定為 *0* ，以啟用 **[ \<Source Control Server> 啟動**] 功能表選項、設定為 [ *1* ] 以停用功能表選項，並設定為 [ *2* ] 以隱藏功能表選項。 如果未出現這個登錄專案，預設行為是顯示功能表選項。

   | 範例登錄專案 | 範例值 |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. 在 [**軟體**] 子機碼中的 **HKEY_LOCAL_MACHINE** 機碼下新增子機碼（ **SourceCodeControlProvider**）。

    在這個子機碼底下，登錄專案 **ProviderRegKey** 會設定為字串，代表您在步驟1中放置於登錄中的子機碼。 此模式是 **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey**  =  *SOFTWARE \\<公司名稱 \> \\<的產品 \> 名稱*。

    以下是此子機碼的範例內容。

   |登錄項目|範例值|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > 您的原始檔控制外掛程式將使用相同的子機碼和專案名稱，但值會不同。

4. 在 **SourceCodeControlProvider** 子機碼底下建立名為 **InstalledSCCProviders** 的子機碼，然後在該子機碼下放置一個專案。

    此專案的名稱是提供者的使用者可讀取名稱 (與針對 SCCServerName 專案) 指定的值相同，且值同樣地是在步驟1中建立的子機碼。 模式是 **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<顯示名稱 \>**  =  *軟體 \\<公司名稱 \> \\<產品名稱 \>*。

    例如：

   |範例登錄專案|範例值|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > 您可以用這種方式註冊多個原始檔控制外掛程式。 這是 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 尋找所有安裝的原始檔控制外掛程式 API 型外掛程式的方式。

## <a name="how-an-ide-locates-the-dll"></a>IDE 如何找到 DLL
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 有兩種方式可以尋找原始檔控制外掛程式 DLL：

- 尋找預設的原始檔控制外掛程式，然後以無訊息方式連接到該外掛程式。

- 尋找所有已註冊的原始檔控制外掛程式，使用者從中選擇其中一個外掛程式。

  若要以第一種方式找出 DLL，IDE 會在專案 **ProviderRegKey** 的 **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** 子機碼下查看。 這個專案的值會指向另一個子機碼。 然後，IDE 會在 **HKEY_LOCAL_MACHINE** 下的第二個子機碼中尋找名為 **SccServerPath** 的專案。 此專案的值會將 IDE 指向 DLL。

> [!NOTE]
> IDE 不會從相對路徑載入 Dll (例如 *.\NewProvider.DLL*) 。 您必須指定 DLL 的完整路徑 (例如 *c:\Providers\NewProvider.DLL*) 。 這可以防止載入未授權或模擬的外掛程式 Dll，進而增強 IDE 的安全性。

 若要以第二種方式找出 DLL，IDE 會在 **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** 子機碼中查看所有專案。 每個專案都有名稱和值。 IDE 會向使用者顯示這些名稱的清單。 當使用者選擇名稱時，IDE 會尋找指向子機碼之選取名稱的值。 IDE 會在 **HKEY_LOCAL_MACHINE** 底下的子機碼中尋找名為 **SccServerPath** 的專案。 該專案的值會將 IDE 指向正確的 DLL。

 原始檔控制外掛程式需要支援兩種方式來尋找 DLL，因此會設定 **ProviderRegKey** 來覆寫任何先前的設定。 更重要的是，它必須將自己加入至 **InstalledSccProviders** 清單，讓使用者可以選擇要使用的原始檔控制外掛程式。

> [!NOTE]
> 因為使用了 **HKEY_LOCAL_MACHINE** 金鑰，所以只能在指定的電腦上將一個原始檔控制外掛程式註冊為預設的原始檔控制外掛程式 (不過，可 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 讓使用者判斷要實際針對特定解決方案) 實際使用的原始檔控制外掛程式。 在您的安裝過程中，請檢查是否已設定原始檔控制外掛程式;如果是的話，請詢問使用者是否要將新的原始檔控制外掛程式安裝為預設值。 在卸載期間，請勿移除 **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider** 中所有原始檔控制外掛程式通用的其他登錄子機碼。只移除您特定的 SCC 子機碼。

## <a name="how-the-ide-detects-version-1213-support"></a>IDE 如何偵測 1.2/1.3 版的支援
 如何偵測 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 外掛程式是否支援原始檔控制外掛程式 API 版本1.2 和1.3 的功能？ 若要宣告 advanced 功能，原始檔控制外掛程式必須執行對應的函式：

 首先，藉 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 由呼叫 [SccGetVersion](../../extensibility/sccgetversion-function.md)來檢查傳回的值。 它必須大於或等於1.2。

 接下來，藉 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 由檢查 `lpSccCaps` [SccInitialize](../../extensibility/sccinitialize-function.md)上的引數，判斷是否支援特定的新功能。

 如果上述兩個條件都符合，則可以呼叫1.2 和1.3 版中支援的新函式。

## <a name="see-also"></a>另請參閱
- [開始使用原始檔控制外掛程式](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
