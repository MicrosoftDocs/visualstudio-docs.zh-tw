---
title: Windows 安裝程式基礎知識 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aeea0b17a3c234bb7670642fb9ae0a442c9d60cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703422"
---
# <a name="windows-installer-basics"></a>Windows Installer 基本概念
Windows 安裝程式在使用者的電腦上安裝和卸載應用程式或軟體產品,以稱為 Windows 安裝程式元件(有時稱為 WIC 或只是元件)的單位執行這些任務。 GUID 識別每個 WIC,這是使用 Windows 安裝程式的安裝和引用計數的基本單元。

 有關 Windows 安裝程式的全面文件,請參閱平臺 SDK 主題[「Windows 安裝程式](/previous-versions/2kt85ked(v=vs.120))」。

## <a name="authoring-a-vspackage"></a>製作音 VS 套件
 Windows 安裝程式使用安裝包,其中包含 Windows 安裝程式安裝、卸載或修復產品以及運行安裝使用者介面 (UI) 所需的資訊。 每個安裝包都包含一個 .msi 檔,該檔包含安裝資料庫、摘要資訊流和安裝各個部分的數據流。 要使用安裝程式,必須編寫安裝。 由於安裝程式圍繞元件的概念組織安裝,並將有關安裝的資訊儲存在關係資料庫中,因此創作安裝包的過程大致需要以下步驟:

1. 規劃設置創作以支援版本控制和並行策略。

2. 標識要呈現給使用者的功能。

3. 將 VS 包和依賴項組織到元件中。

4. 使用資訊填充安裝資料庫。

5. 驗證安裝包。

   本文檔主要涉及該過程的第一個和第三步。 在這些步驟中,您將 VSPackage 功能組織到 WIC 中,以便可以制定版本控制和服務[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]策略,以考慮的後續版本。 其餘三個步驟詳在平臺 SDK 中的 Windows 安裝程序文檔中。

## <a name="key-terms"></a>主要詞彙：
 以下是與 Windows 安裝程式技術相關的關鍵術語的定義。

 可能安裝到計算機的資源檔、註冊表項、快捷方式等。 這些資源以邏輯方式分組到 Windows 安裝程式元件中。

 Windows 安裝程式元件 (WIC) 表示作為設備安裝並卸載的相關資源的邏輯分組的基本安裝單元。 Windows 安裝程式元件由唯一元件 ID 或 GUID 識別。 此外,Windows 安裝程式在 WIC 級別保持其引用計數。 為了獲得最大的版本控制靈活性,在給定的 WIC 中只包含一個主資源(如 DLL)。 請注意,在標識和填充WIC、為其提供GUID並部署它後,無法更改其組成。 有關詳細資訊,請參閱[將應用程式組織到元件](/windows/desktop/Msi/organizing-applications-into-components)中。

 包(Redist 包)一個部署單元,由 .msi 檔和外部源文件組成,此檔可能會指向該檔。 包包含 Windows 安裝程式運行 UI 以及安裝或卸載應用程式所需的所有資訊。

 .msi 檔案 A COM 結構化儲存檔案,其中包含安裝應用程式所需的說明和資料。 每個包至少包含一個 .msi 檔。 .msi 檔包含安裝程式資料庫、摘要資訊流,以及可能一個或多個轉換和內部源檔。 要安裝的檔案可以壓縮到機櫃中並存儲在 .msi 檔案中的流中,也可以存儲在源介質上的 .msi 檔案之外,進行壓縮或未壓縮。 關於詳細資訊,請參閱[Windows 安裝程式檔副檔名](/windows/desktop/Msi/windows-installer-file-extensions)。

## <a name="windows-installer-rules-enforcement"></a>Windows 安裝程式規則強制
 兩組規則確定通過設置的元件部署資源。 一個規則集由 Windows 安裝程式本身維護,而應強制第二個集作為安裝作者。

> [!NOTE]
> 僅當運行 .msi 檔案的驗證時,才會強制實施 Windows 安裝程式規則。 不過,請注意,應將這些規則視為最佳實踐。 有關詳細資訊,請參閱[驗證安裝資料庫](/windows/desktop/Msi/validating-an-installation-database)和[套件驗證](/windows/desktop/Msi/package-validation)。

#### <a name="installer-enforced-rules"></a>安裝程式強制規則

- 給定元件中的所有檔都必須安裝到同一目錄。 相反,安裝到獨立資料夾的檔必須屬於單獨的元件。

- 每個元件只能有一個密鑰路徑。 密鑰路徑只是表示整個元件的檔或註冊表項。

#### <a name="component-provider-responsibilities"></a>元件-供應商職責

- 在後續版本中可能單獨提供的任何兩個資源都應存在於單獨的元件中。 僅當確定這些資源永遠不會單獨發貨時,才應將資源分組到同一元件中。 事實上,建議所有主資源(例如 DLL)始終存在於單獨的 WIC 中。 有關詳細資訊,請參閱[定義安裝程式元件](/windows/desktop/Msi/defining-installer-components)。

- 任何版本化資源都不應在多個WIC中發貨。

## <a name="see-also"></a>另請參閱
- [如果組件規則斷開,會發生什麼情況?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
