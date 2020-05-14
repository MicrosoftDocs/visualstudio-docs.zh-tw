---
title: 如何:安裝原始程式碼管理外掛程式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c0ac87aec3d6ac2532909772238e020e33bf78f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707998"
---
# <a name="how-to-install-a-source-control-plug-in"></a>如何:安裝原始碼管理外掛程式
建立原始碼管理外掛程式包括三個步驟:

1. 使用本文件的源碼管理外掛程式 API 引用部分中定義的函數創建 DLL。

2. 實現原始程式碼管理外掛程式 API 定義的功能。 調用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]時,使介面和對話框可從外掛程式。

3. 通過進行適當的註冊表項來註冊 DLL。

## <a name="integration-with-visual-studio"></a>與 Visual Studio 整合
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援符合原始碼管理外掛程式 API 的原始程式碼管理外掛程式。

### <a name="register-the-source-control-plug-in"></a>註冊原始程式管理外掛程式
 在正在執行的整合式開發環境 (IDE) 可以呼叫原始程式碼管理系統之前,必須首先找到匯出 API 的原始程式碼管理外掛程式 DLL。

#### <a name="to-register-the-source-control-plug-in-dll"></a>註冊原始程式碼管理外掛程式 DLL

1. 在 **「軟體」** 子鍵中**HKEY_LOCAL_MACHINE**鍵下添加兩個條目,該鍵指定公司名稱子鍵後跟產品名稱子鍵。 該模式是**HKEY_LOCAL_MACHINE_\\\<軟體 公司\\\<名稱>產品名稱\\\<>條目>** = *值*。 這兩個項目始終稱為**SCCServer 名稱**和**SCCServerPath**。 每個字串都是常規字串。

    例如,如果您的公司名稱是 Microsoft,並且原始程式碼管理產品名為 SourceSafe,則此註冊表路徑將為**HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_SourceSafe**。 在此子鍵中,第一個條目**SCCServerName**是用戶可讀的字串,用於命名您的產品。 第二個條目**SCCServerPath**是 IDE 應連接到的原始程式碼管理外掛程式 DLL 的完整路徑。 下面提供了範例註冊表項:

   |範例註冊表條目|範例值|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE_SOFTWARE_微軟\來源安全\SCCServer名稱|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE_SOFTWARE_微軟\來源安全\SCCServer路徑|*c:\vss_win32_sscc.dll*|

   > [!NOTE]
   > SCCServerPath 是源安全外掛程式的完整路徑。 原始程式碼管理外掛程式將使用不同的公司和產品名稱,但相同的註冊表輸入路徑。

2. 以下可選註冊表項可用於修改原始程式碼管理外掛程式的行為。 這些項目與**SccServerName**和**SccServerPath**位於同一個子鍵中。

   - 如果您不希望原始程式碼管理外掛[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]程式出現在的**外掛程式選擇**清單中,可以使用**HideInVisualStudio 註冊表**。 此項目還將影響自動切換到原始程式碼管理外掛程式。 此項的一個可能用途是,如果提供一個原始程式碼管理包,以取代原始程式碼管理外掛程式,但您希望使用戶更容易從使用原始程式碼管理外掛程式遷移到原始程式碼管理包。 安裝原始程式碼管理包時,它會設置此註冊表項,該註冊表項將隱藏外掛程式。

      **HideInVisualStudio**是一個 DWORD 值,設置為*1*以隱藏外掛程式或*0*以顯示外掛程式。 如果未顯示註冊表項,則默認行為是顯示外掛程式。

   - **"禁用SccManager**註冊表"可用於禁用或隱藏啟動**\<源控制伺服器>** 功能表選項,該功能表通常出現在 **'檔案** > **源控制"** 子功能表下。 選擇此功能表選項將調用[SccRunScc](../../extensibility/sccrunscc-function.md)函數。 源代碼管理外掛程式可能不支援外部程式,因此您可能需要禁用甚至隱藏 **「啟動」** 選單選項。

      **禁用SccManager**是一個 DWORD 值,設置為*0*以啟用**啟動\<源控制伺服器>** 選單選項,設置為*1*以禁用功能表選項,並設置為*2*以隱藏選單選項。 如果未顯示此註冊表項,則默認行為是顯示功能表選項。

   | 範例註冊表項 | 範例值 |
   | - |--------------|
   | HKEY_LOCAL_MACHINE_SOFTWARE_微軟_來源安全_隱藏視覺工作室 | 1 |
   | HKEY_LOCAL_MACHINE_SOFTWARE_微軟\來源安全\禁用Scc管理員 | 1 |

3. 在**軟體**子鍵中**HKEY_LOCAL_MACHINE**鍵下添加子鍵 **「原始程式碼控制提供者**」。

    在此子鍵下,註冊表項**提供程式 RegKey**設置為一個字串,該字串表示您在步驟 1 中放置在註冊表中的子鍵。 模式是**HKEY_LOCAL_MACHINE_SOFTWARE_原始碼控制提供者\供應商RegKey** = *\\軟體\>\\\><公司名称<产品名称*。

    以下是此子鍵的示例內容。

   |登錄項目|範例值|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE_SOFTWARE_原始程式碼控制提供者\供應商雷吉|軟體\微軟\來源安全|

   > [!NOTE]
   > 原始程式碼管理外掛程式將使用相同的子鍵和條目名稱,但值將不同。

4. 在**原始碼管理提供程式**子鍵下建立名為 **「已安裝SCC提供程式」** 的子鍵,然後將一個項目放在該子鍵下。

    此條目的名稱是提供程式的用戶可讀名稱(與為 SCCServerName 條目指定的值相同),該值再次成為步驟 1 中創建的子鍵。 模式是**HKEY_LOCAL_MACHINE_SOFTWARE_源代碼控制提供程式\已安裝SCC\\供應商<顯示名稱\>***\\\>\\\>* = 軟體<公司名稱<產品名稱。

    例如：

   |範例註冊表項|範例值|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE_SOFTWARE_原始程式碼控制提供者\已安裝SCC供應商\微軟視覺源安全|軟體\微軟\來源安全|

   > [!NOTE]
   > 可以以這種方式註冊多個原始程式碼管理外掛程式。 這是查找[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]所有已安裝的基於 API 的原始程式碼管理外掛程式的方式。

## <a name="how-an-ide-locates-the-dll"></a>IDE 如何定位 DLL
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 有兩種尋找原始碼管理外掛程式 DLL 的方法:

- 查找預設原始程式碼管理外掛程式並靜默連接到它。

- 查找使用者從中選擇一個的所有已註冊的原始程式碼管理外掛程式。

  要以第一種方式定位 DLL,IDE 將查找項目**提供程式 RegKey****的HKEY_LOCAL_MACHINE\軟體\原始碼管理提供程式**子鍵下。 此條目的值指向另一個子鍵。 然後,IDE 在**HKEY_LOCAL_MACHINE**下的第二個子鍵中查找名為**SccServerPath**的條目。 此條目的值將 IDE 指向 DLL。

> [!NOTE]
> IDE 不會從相對路徑載入 DLL(例如 *,._NewProvider.DLL*)。 必須指定 DLL 的完整路徑(例如 *,c:\提供程式\NewProvider.DLL)。* 這通過防止載入未經授權的或類比的外掛程式 DLL 來增強 IDE 的安全性。

 要以第二種方式查找 DLL,IDE 會查找所有條目**的HKEY_LOCAL_MACHINE\軟體\原始程式碼管理提供程式\已安裝SCCProviders**子鍵下。 每個條目都有一個名稱和一個值。 IDE 向使用者顯示這些名稱的清單。 當用戶選擇名稱時,IDE 會查找指向子鍵的選定名稱的值。 IDE 在**HKEY_LOCAL_MACHINE**下該子鍵中查找名為**SccServerPath**的條目。 該條目的值將IDE指向正確的DLL。

 源代碼管理外掛程式需要支援找到 DLL 的方法,從而設置**提供程式 RegKey,** 覆蓋任何以前的設置。 更重要的是,它必須將自己添加到**已安裝 Scc 提供程式**清單中,以便用戶可以選擇要使用的原始程式碼管理外掛程式。

> [!NOTE]
> 由於使用了**HKEY_LOCAL_MACHINE**密鑰,因此在給定電腦上只能將一個原始程式碼管理外掛程式註冊為預設原始程式碼管理外掛[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]程式(但是, 允許用戶確定要實際用於特定解決方案的原始程式碼管理外掛程式)。 在安裝過程中,請檢查是否設置了原始程式碼管理外掛程式;如果安裝過程,請檢查是否已設置原始程式碼管理外掛程式。如果是這樣,請詢問使用者是否將安裝的新原始程式碼管理外掛程式設置為預設值。 在卸載期間,不要刪除**HKEY_LOCAL_MACHINE_SOFTWARE_SourceCodeControlProvider**; 中所有原始程式碼外掛程式所共有的其他註冊表子鍵。僅刪除您的特定 SCC 子金鑰。

## <a name="how-the-ide-detects-version-1213-support"></a>IDE 如何檢測版本 1.2/1.3 支援
 如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵測外掛程式是否支援原始程式碼管理外掛程式 API 版本 1.2 和 1.3 功能? 要聲明進階功能,原始程式碼管理外掛程式必須實現相應的功能:

 首先,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通過調用[SccGetVersion](../../extensibility/sccgetversion-function.md)檢查返回的值。 它必須大於或等於1.2。

 接下來,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通過`lpSccCaps`檢查[Scc 初始化](../../extensibility/sccinitialize-function.md)上的參數來確定是否支援特定的新功能。

 如果滿足這兩個條件,則可以調用版本 1.2 和 1.3 中支援的新功能。

## <a name="see-also"></a>另請參閱
- [開始使用原始碼管理外掛程式](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
