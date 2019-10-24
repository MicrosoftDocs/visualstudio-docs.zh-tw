---
title: Windows Installer 基本概念 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a6e671b8b5a20d10624e8f89b601c23087237d2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721501"
---
# <a name="windows-installer-basics"></a>Windows Installer 基本概念
Windows Installer 會在使用者的電腦上安裝和卸載應用程式或軟體產品，以稱為 Windows Installer 元件（有時稱為 WICs 或只是元件）的單位來執行這些工作。 GUID 會識別每個 WIC，這是使用 Windows Installer 安裝的基本單位和參考計數。

 如需 Windows Installer 的完整檔，請參閱 Platform SDK 主題， [Windows Installer](/previous-versions/2kt85ked(v=vs.120))。

## <a name="authoring-a-vspackage"></a>撰寫 VSPackage
 Windows Installer 使用安裝套件，其中包含 Windows Installer 需要安裝、卸載或修復產品，以及執行安裝程式使用者介面（UI）的資訊。 每個安裝套件都包含一個 .msi 檔案，其中包含安裝資料庫、摘要資訊資料流程，以及安裝各部分的資料流程。 若要使用安裝程式，您必須撰寫安裝。 因為安裝程式會根據元件的概念來組織安裝，並將安裝的相關資訊儲存在關係資料庫中，所以廣泛撰寫安裝套件的程式需要執行下列步驟：

1. 規劃您的安裝程式撰寫，以支援您的版本控制和並存策略。

2. 識別要呈現給使用者的功能。

3. 將 VSPackage 和相依性組織成元件。

4. 在安裝資料庫中填入資訊。

5. 驗證安裝套件。

   本檔主要涉及程式的第一個和第三個步驟。 在這些步驟中，您會將 VSPackage 功能組織成 WICs，以便將您的版本控制和服務策略納入考慮，以將後續版本的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 其餘三個步驟會在 Platform SDK 的 Windows Installer 檔中詳細說明。

## <a name="key-terms"></a>主要詞彙
 以下是與 Windows Installer 技術相關之重要詞彙的定義。

 可以安裝在電腦上的資源檔、登錄機碼、快捷方式等等。 這些資源會以邏輯方式分組到 Windows Installer 元件中。

 Windows Installer 元件（WIC）基本安裝單位，代表以一個單位安裝和卸載的相關資源的邏輯群組。 Windows Installer 元件是以唯一的元件識別碼或 GUID 來識別。 此外，Windows Installer 會在 WIC 層級維護其參考計數。 如需最大版本控制彈性，請在指定的 WIC 中包含不只一個主要資源（例如 DLL）。 請注意，在您識別並填入 WIC 之後，請為它提供 GUID 並加以部署，您無法變更其組合。 如需詳細資訊，請參閱將[應用程式組織成元件](/windows/desktop/Msi/organizing-applications-into-components)。

 封裝（可轉散發套件）部署的單位，其中包含這個檔案可能指向的 .msi 檔案和外部來源檔案。 套件包含 Windows Installer 執行 UI 以及安裝或卸載應用程式時所需的所有資訊。

 .msi 檔案是 COM 結構化的儲存體檔案，其中包含安裝應用程式所需的指示和資料。 每個套件都包含至少一個 .msi 檔案。 .Msi 檔案包含安裝程式資料庫、摘要資訊資料流程，而且可能有一或多個轉換和內部來源檔案。 要安裝的檔案可以壓縮成封包，並儲存在 .msi 檔的資料流程中，或儲存、壓縮或未壓縮的來源媒體上的 .msi 檔案外。 如需詳細資訊，請參閱[Windows Installer 副檔名](/windows/desktop/Msi/windows-installer-file-extensions)。

## <a name="windows-installer-rules-enforcement"></a>強制執行 Windows Installer 規則
 兩組規則會決定透過您的安裝程式元件來部署資源。 其中一個規則集是由 Windows Installer 本身維護，而您應將第二組強制執行為安裝作者。

> [!NOTE]
> 只有當您執行 .msi 檔案的驗證時，才會強制執行 Windows Installer 規則。 儘管如此，您匯將這些規則視為最佳作法。 如需詳細資訊，請參閱[驗證安裝資料庫](/windows/desktop/Msi/validating-an-installation-database)和[封裝驗證](/windows/desktop/Msi/package-validation)。

#### <a name="installer-enforced-rules"></a>安裝程式強制執行的規則

- 指定元件中的所有檔案都必須安裝到相同的目錄。 相反地，安裝在不同資料夾的檔案必須屬於不同的元件。

- 每個元件只能有一個金鑰路徑。 金鑰路徑只是代表整個元件的檔案或登錄機碼。

#### <a name="component-provider-responsibilities"></a>元件提供者責任

- 可能會分別在後續版本中運送的任何兩個資源，都應該存在於不同的元件中。 只有在您確定這些資源永遠不會另行寄送時，才應該將資源分組成相同的元件。 事實上，建議所有的主要資源（例如 Dll）一律存在於個別的 WICs 中。 如需詳細資訊，請參閱[定義安裝程式元件](/windows/desktop/Msi/defining-installer-components)。

- 沒有任何已建立版本的資源應該在一個以上的 WIC 中出貨。

## <a name="see-also"></a>請參閱
- [當元件規則中斷時，會發生什麼事？](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)