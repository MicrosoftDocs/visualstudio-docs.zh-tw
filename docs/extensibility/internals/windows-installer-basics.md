---
title: Windows 安裝程式的基本概念 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 8fba35aba1e1947ee4eeeb59ca2225253e2aa3a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="windows-installer-basics"></a>Windows 安裝程式的基本概念
Windows Installer 安裝和解除安裝應用程式或軟體產品，使用者的電腦上執行這些工作單位稱為 （有時稱為 WICs 或只是元件） 的 Windows Installer 元件。 GUID 識別每個 WIC，也就是安裝和參考計數，若是使用 Windows Installer 設定的基本單位。  
  
 完整的 Windows Installer 的文件，請參閱 Platform SDK 主題[Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx)。  
  
## <a name="authoring-a-vspackage"></a>撰寫 VSPackage  
 Windows 安裝程式會使用安裝封裝，其中包含 Windows 安裝程式需要安裝、 解除安裝或修復產品，並執行安裝程式使用者介面 (UI) 的資訊。 每個安裝套件包含.msi 檔案，其中包含安裝資料庫、 摘要資訊資料流，以及安裝的各個部分的資料流。 若要使用安裝程式，您必須撰寫安裝。 安裝程式會安裝元件的概念來組織，和將安裝的相關資訊儲存在關聯式資料庫，因為廣泛地撰寫安裝封裝的程序牽涉到下列步驟：  
  
1.  規劃您的安裝撰寫以支援您的版本控制和並行的策略。  
  
2.  識別要呈現給使用者的功能。  
  
3.  為元件組織 VSPackage 和相依性。  
  
4.  填入安裝資料庫的資訊。  
  
5.  驗證安裝的封裝。  
  
 這份文件是主要被有關程序的第一個和第三個步驟。 在這些步驟將組織 VSPackage 功能到 WICs 讓您可以將您的版本控制和服務策略的後續版本的框[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 剩餘的三個步驟會包含在 Windows 安裝程式文件中的平台 SDK 的詳細資料。  
  
## <a name="key-terms"></a>主要詞彙  
 下面是 Windows Installer 技術相關的重要詞彙的定義。  
  
 資源  
 檔案、 登錄機碼、 快速鍵、 或，依此類推，可能會安裝到電腦。 這些資源會以邏輯方式分組為 Windows Installer 元件。  
  
 Windows Installer 元件 (WIC)  
 代表已安裝及解除安裝當做一個單位的相關資源的邏輯群組的安裝的基本單位。 Windows Installer 元件會識別元件的唯一識別碼或 GUID。 此外，Windows Installer 會維護其參考計數在 WIC 層級。 最大版本控制的彈性，包含一個以上的主要資源，例如 DLL，在給定 WIC。 請注意，找出並填入 WIC，提供 GUID，並將其部署之後，您無法變更其構造。 如需詳細資訊，請參閱[組織應用程式元件](http://msdn.microsoft.com/library/aa370561.aspx)。  
  
 封裝 （可轉散發套件）  
 .msi 檔案和外部的原始程式檔可能會指向這個檔案所組成的部署單位。 封裝包含 Windows 安裝程式必須執行 UI 和安裝或解除安裝應用程式的所有資訊。  
  
 .msi 檔案  
 COM 結構化儲存體檔案，其中包含的指示和安裝應用程式所需的資料。 每個套件包含至少一個.msi 檔案。 .msi 檔案包含安裝程式資料庫、 摘要資訊資料流，以及可能是一個或多個轉換內部的原始程式檔。 要安裝的檔案可以壓縮成封包和儲存在.msi 檔案中的資料流或儲存、 壓縮，或未壓縮，在來源媒體上的.msi 檔案外部。 如需詳細資訊，請參閱[Windows Installer 檔案副檔名](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx)。  
  
## <a name="windows-installer-rules-enforcement"></a>Windows Installer 規則強制  
 這兩組規則決定部署透過您的安裝程式元件的資源。 一個規則集是由 Windows Installer 本身，維護，應強制執行第二組安裝在撰寫時。  
  
> [!NOTE]
>  只有當您執行的.msi 檔案的驗證，就會發生 Windows Installer 規則強制執行。 不過，您會 cautioned 這些規則視為最佳作法。 如需詳細資訊，請參閱[驗證安裝資料庫](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx)和[封裝驗證](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx)。  
  
#### <a name="installer-enforced-rules"></a>安裝程式強制執行規則  
  
-   指定的元件中的所有檔案必須都安裝到相同的目錄。 相反地，安裝在不同的資料夾的檔案必須屬於分隔元件。  
  
-   可以有只有一個機碼路徑中的每個元件。 機碼路徑是只要檔案或登錄機碼，表示整個元件。  
  
#### <a name="component-provider-responsibilities"></a>元件提供者的責任  
  
-   任何兩個資源可能會在後續版本中的個別付應存在於不同的元件。 資源應該只在您確定時，這些資源將永遠不會隨附個別分在同一個元件。 事實上，我們建議所有的主要資源 (例如 Dll) 中個別 WICs 永遠存在。 如需詳細資訊，請參閱[定義安裝程式元件](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx)。  
  
-   沒有建立版本的資源曾經應該在一個以上的 WIC 交運。  
  
## <a name="see-also"></a>另請參閱  
 [元件規則已中斷，則會發生什麼情況？](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)