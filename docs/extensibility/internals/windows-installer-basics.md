---
title: Windows Installer 基本概念 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9eff9cb08c07c33ff2af707501f1ee6fac2e01da
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914740"
---
# <a name="windows-installer-basics"></a>Windows Installer 基本概念
Windows 安裝程式安裝和解除安裝應用程式或使用者的電腦上的軟體產品執行這些工作單位，稱為 Windows 安裝程式元件 （有時稱為 WICs 或只是元件）。 GUID 會識別每個 WIC，也就是安裝和參考計數來設定使用 Windows 安裝程式的基本單位。  
  
 Windows 安裝程式的完整文件，請參閱 Platform SDK 主題[Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx)。  
  
## <a name="authoring-a-vspackage"></a>撰寫 VSPackage  
 Windows 安裝程式會使用安裝封裝，其中包含 Windows 安裝程式必須安裝、 解除安裝或修復產品，並執行安裝程式使用者介面 (UI) 的資訊。 每個安裝套件包含.msi 檔案，其中包含安裝資料庫、 摘要資訊資料流，以及安裝的各個部分的資料流。 若要使用安裝程式，您必須編寫安裝。 因為安裝程式會安裝元件的概念為中心的組織，並將安裝的相關資訊儲存在關聯式資料庫，廣泛地撰寫安裝套件的程序需要下列步驟：  
  
1. 規劃您的安裝程式編寫，以支援您的版本控制和並排顯示的策略。  
  
2. 識別要呈現給使用者的功能。  
  
3. 組織成元件的 VSPackage 和相依性。  
  
4. 在資料庫中填入安裝資訊。  
  
5. 驗證安裝的封裝。  
  
   這份文件主要涉及程序的第一個和第三個步驟。 在這些步驟將組織 VSPackage 功能到 WICs 讓您可以將您的版本控制和服務策略以迎合的後續版本框[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 其餘的三個步驟所述的平台 SDK 中的 Windows 安裝程式文件中的詳細資料。  
  
## <a name="key-terms"></a>主要詞彙  
 以下是 Windows Installer 技術的相關的重要詞彙的定義。  
  
 資源  
 檔案、 登錄機碼、 捷徑、 或，依此類推，可能會安裝到電腦。 這些資源會以邏輯方式分組，為 Windows 安裝程式元件。  
  
 Windows 安裝程式元件 (WIC)  
 表示已安裝及解除安裝當做一個單位的相關資源的邏輯群組的安裝基本的單位。 Windows 安裝程式元件是唯一的元件識別碼或 GUID 所識別。 此外，Windows 安裝程式會維護它的參考計數 WIC 層級。 最大的版本控制彈性，請在 指定 WIC 中包含不超過一個主要資源的詳細資訊，例如的 DLL。 請注意，識別並填入 WIC、 為它提供的 GUID，並將其部署之後，您無法變更其組合。 如需詳細資訊，請參閱 <<c0> [ 組織的應用程式元件](/windows/desktop/Msi/organizing-applications-into-components)。  
  
 套件 （可轉散發套件）  
 .msi 檔案和外部的原始程式檔可能會指向這個檔案所組成的部署單位。 套件包含 Windows 安裝程式需要執行 UI 和安裝或解除安裝應用程式的所有資訊。  
  
 .msi 檔案  
 COM 結構化儲存體檔案，其中包含的指示和安裝應用程式所需的資料。 每個套件都包含至少一個.msi 檔案。 將.msi 檔案包含安裝程式資料庫，摘要資訊資料流，可能是一或多個轉換和內部的原始程式檔。 要安裝檔案可以是壓縮成封包和.msi 檔案中的資料流中儲存或儲存、 壓縮，或未壓縮，外部來源媒體上將.msi 檔案。 如需詳細資訊，請參閱 < [Windows Installer 檔案副檔名](/windows/desktop/Msi/windows-installer-file-extensions)。  
  
## <a name="windows-installer-rules-enforcement"></a>Windows Installer 規則強制執行  
 兩組規則會決定部署透過您的安裝程式元件的資源。 雖然您應該會強制執行第二個集合，身為安裝的作者，Windows 安裝程式本身，會維護一個規則集。  
  
> [!NOTE]
>  只有當您執行的.msi 檔案的驗證，就會發生 Windows Installer 規則強制執行。 不過，您會 cautioned 這些規則視為最佳做法。 如需詳細資訊，請參閱 <<c0> [ 驗證安裝資料庫](/windows/desktop/Msi/validating-an-installation-database)並[封裝驗證](/windows/desktop/Msi/package-validation)。  
  
#### <a name="installer-enforced-rules"></a>安裝程式強制執行規則  
  
-   指定的元件中的所有檔案必須都安裝到相同的目錄。 相反地，安裝在不同的資料夾的檔案必須屬於不同的元件。  
  
-   可以有只有一個機碼的路徑，每個元件。 機碼路徑是只是檔案或登錄機碼，表示整個元件。  
  
#### <a name="component-provider-responsibilities"></a>元件提供者的責任  
  
-   分開可能在後續版本中提供的任何兩個資源應該位於個別的元件。 資源應該分組到同一個元件，只有當您確定這些資源將永遠不會分開的提供時，才。 事實上，我們建議所有的主要資源 (例如 Dll) 一律存在於個別 WICs。 如需詳細資訊，請參閱 <<c0> [ 定義安裝程式元件](/windows/desktop/Msi/defining-installer-components)。  
  
-   沒有建立版本的資源應該曾經出貨中一個以上的 WIC。  
  
## <a name="see-also"></a>另請參閱  
 [元件規則已中斷，會發生什麼事？](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)