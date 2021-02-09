---
title: Windows Installer 基本概念 |Microsoft Docs
description: 瞭解 Windows Installer 在安裝 VSPackage 時使用，包括將 VSPackage 功能組織成 Windows Installer 元件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4081c79b7492e369e19187a099bf975275cb371c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869488"
---
# <a name="windows-installer-basics"></a>Windows Installer 基本概念
Windows Installer 在使用者的電腦上安裝和卸載應用程式或軟體產品，以稱為 Windows Installer 元件的單位來執行這些工作 (有時候稱為 WICs 或只是) 的元件。 GUID 會識別每個 WIC，也就是使用 Windows Installer 進行安裝的基本安裝單位和參考計數。

 如需 Windows Installer 的完整檔，請參閱 Platform SDK 主題 [Windows Installer](/previous-versions/2kt85ked(v=vs.120))。

## <a name="authoring-a-vspackage"></a>撰寫 VSPackage
 Windows Installer 使用安裝套件，其中包含 Windows Installer 需要安裝、卸載或修復產品，以及執行安裝程式使用者介面 (UI) 的資訊。 每個安裝套件都包含一個 .msi 檔案，其中包含安裝資料庫、摘要資訊資料流程，以及安裝的各部分的資料流程。 若要使用安裝程式，您必須撰寫安裝。 因為安裝程式會根據元件的概念來組織安裝，並且將安裝的相關資訊儲存在關係資料庫中，所以撰寫安裝套件的程式會廣泛地牽涉到下列步驟：

1. 規劃您的安裝程式撰寫，以支援您的版本控制和並存策略。

2. 識別要呈現給使用者的功能。

3. 將 VSPackage 和相依性組織為元件。

4. 填入安裝資料庫中的資訊。

5. 驗證安裝套件。

   這份檔主要是在處理常式的第一個和第三個步驟。 在這些步驟中，您會將 VSPackage 功能組織成 WICs，讓您可以將版本控制和服務策略納入考慮，以考慮後續版本的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 其餘三個步驟會在 Platform SDK 的 Windows Installer 檔中詳細說明。

## <a name="key-terms"></a>主要詞彙：
 以下是與 Windows Installer 技術相關之重要詞彙的定義。

 可能安裝在電腦上的資源檔、登錄機碼、快捷方式等等。 這些資源會以邏輯方式分組為 Windows Installer 元件。

 Windows Installer 元件 (WIC) 基本安裝單位，代表以一個單位安裝和卸載之相關資源的邏輯群組。 Windows Installer 元件是以唯一的元件識別碼或 GUID 來識別。 此外，Windows Installer 會在 WIC 層級維護其參考計數。 如需最大版本控制彈性，請在指定的 WIC 中包含一個以上的主要資源，例如 DLL。 請注意，在您識別並填入 WIC 之後，請將它命名為 GUID，然後加以部署，您就無法變更它的組合。 如需詳細資訊，請參閱將 [應用程式組織成元件](/windows/desktop/Msi/organizing-applications-into-components)。

 封裝 (可轉散發套件) 包含 .msi 檔案的部署單位，以及此檔案可能指向的外部原始程式檔。 套件包含 Windows Installer 執行 UI 以及安裝或卸載應用程式所需的所有資訊。

 .msi 檔案是包含安裝應用程式所需之指示和資料的 COM 結構化儲存體檔案。 每個封裝至少包含一個 .msi 檔案。 .Msi 檔案包含安裝程式資料庫、摘要資訊資料流程，以及可能有一或多個轉換和內部原始程式檔。 要安裝的檔案可以壓縮成封包，並儲存在 .msi 檔案的資料流程中，或是儲存、壓縮或解壓縮，在來源媒體的 .msi 檔案之外。 如需詳細資訊，請參閱 [Windows Installer 的副檔名](/windows/desktop/Msi/windows-installer-file-extensions)。

## <a name="windows-installer-rules-enforcement"></a>強制執行規則 Windows Installer
 有兩組規則會透過您的安裝程式元件來決定資源的部署。 其中一個規則集是由 Windows Installer 本身所維護，而您應該強制將第二個集合做為安裝作者。

> [!NOTE]
> 只有當您執行 .msi 檔案的驗證時，才會強制執行 Windows Installer 規則。 不過，您匯將這些規則視為最佳做法。 如需詳細資訊，請參閱 [驗證安裝資料庫](/windows/desktop/Msi/validating-an-installation-database) 和 [封裝驗證](/windows/desktop/Msi/package-validation)。

#### <a name="installer-enforced-rules"></a>Installer-Enforced 規則

- 指定元件中的所有檔案都必須安裝在相同的目錄中。 相反地，安裝至個別資料夾的檔案必須屬於個別的元件。

- 每個元件只能有一個金鑰路徑。 金鑰路徑只是代表整個元件的檔案或登錄機碼。

#### <a name="component-provider-responsibilities"></a>Component-Provider 責任

- 可能在後續版本中個別傳送的任何兩個資源，都應該存在於不同的元件中。 只有在您確定這些資源永遠不會個別運送時，才應該將資源群組至相同的元件。 事實上，建議所有的主要資源 (Dll，例如) 一律存在於不同的 WICs 中。 如需詳細資訊，請參閱 [定義安裝程式元件](/windows/desktop/Msi/defining-installer-components)。

- 沒有任何已建立版本的資源應該在一個以上的 WIC 中送出。

## <a name="see-also"></a>另請參閱
- [如果元件規則中斷，會發生什麼事？](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
