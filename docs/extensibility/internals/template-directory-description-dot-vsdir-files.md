---
title: "範本目錄的描述 (。Vsdir) 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 739dd0d41fb63c4993dad0d66737aaada1cf01c4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="template-directory-description-vsdir-files"></a>範本目錄的描述 (。Vsdir) 檔案
範本的目錄描述檔案 (.vsdir) 是文字檔案，可讓整合式的開發環境 (IDE) 以顯示與您在對話方塊中的專案相關聯的範本檔案、 精靈.vsz 檔案和資料夾。 內容包括每個檔案或資料夾的一筆記錄。 參考位置中的所有.vsdir 檔案會都合併，雖然只有一個.vsdir 檔案通常提供來描述多個資料夾、 精靈、 或範本檔案。  
  
 資料夾 （子目錄）.vsdir 檔案，與.vsdir 檔案本身中所參考的檔案全部都位於相同的目錄中。 當 IDE 執行精靈，或顯示資料夾或檔案中的**新專案**或**加入新項目**對話方塊方塊中，IDE 會檢查包含執行的檔案，以判斷是否.vsdir 檔案的目錄存在。 如果找到.vsdir 檔案時，IDE 會讀取以判斷它是否包含執行或顯示資料夾或檔案的項目。 如果找到項目，IDE 會在執行精靈或內容的顯示中使用的資訊。  
  
 下列程式碼範例會從檔案 SourceFiles.vsdir 中\<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files 登錄機碼：  
  
```  
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127  
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124  
```  
  
 在此情況下，兩筆記錄會在一個檔案中。 新的一行 （歸位字元） 分隔每一筆記錄。 每一列都代表不同的檔案類型。 管道 (&#124;) 字元會分隔每個記錄中的欄位。 單一目錄中可包含多個具有不同的檔案名稱的.vsdir 檔案，或者您可以擁有一個.vsdir 檔案，每個檔案類型。  
  
## <a name="fields"></a>欄位  
 下表列出每一筆記錄指定的欄位。  
  
|欄位|描述|  
|-----------|-----------------|  
|相對路徑名稱 (RelPathName)|資料夾、 範本或.vsz 檔案，例如 HeaderFile.h 或 MyWizard.vsz 的名稱。 這個欄位也可以用來代表資料夾的名稱。|  
|{clsidPackage}|VSPackage 可讓您存取中的當地語系化字串，例如 LocalizedName、 描述、 IconResourceId 和 SuggestedBaseName，VSPackage 的附屬項目動態連結程式庫 (DLL) 資源的 GUID。 如果未提供 DLLPath，適用於 IconResourceId。 **注意：**這個欄位是選擇性的除非一或多個先前的欄位是資源識別碼。 這個欄位是通常是空白的未當地語系化文字的第三方精靈與對應的.vsdir 檔案。|  
|LocalizedName|範本檔案或精靈的當地語系化的名稱。 這個欄位可以是字串或表單"#ResID 」 資源識別項。 這個名稱會顯示在**加入新項目** 對話方塊。 **注意：**如果 LocalizedName 資源識別項，則 {clsidPackage} 是必要項。|  
|SortPriority|表示此範本檔案或精靈的相對優先權的整數。 例如，如果此項目有值為 1，此項目會顯示其他項目旁的值為 1 和 2 或更大的所有項目排序值前面。<br /><br /> 排序優先順序是相對於相同的目錄中的項目。 相同的目錄中可能有一個以上的.vsdir 檔案。 在此情況下，從所有的項目*。*該目錄中的 vsdir 檔案會合併。 具有相同優先順序的項目所述的顯示名稱不區分大小寫的詞典編纂順序。 `_wcsicmp`函式用來排序項目。<br /><br /> 未在.vsdir 檔中描述的項目包括大於.vsdir 檔案中列出的最高優先順序編號的優先順序數字。 結果是清單的，這些項目所顯示，不論其名稱的結尾。|  
|描述|範本檔案或精靈的當地語系化的描述。 這個欄位可以是字串或表單"#ResID 」 資源識別項。 此字串會出現在**新專案**或**加入新項目**對話方塊中選取項目時。|  
|DLLPath 或者 {clsidPackage}|用來載入的範本檔案或精靈圖示。 圖示會 IconResourceId 載入做為從.dll 或.exe 檔案的資源。 使用完整路徑，或是使用 VSPackage 的 GUID，可以識別此.dll 或.exe 檔案。 實作 VSPackage 的 DLL 用來載入圖示 （不附屬 DLL）。|  
|IconResourceId|中的 DLL 或 VSPackage 的實作會決定要顯示的圖示的 DLL 的資源識別碼。|  
|旗標 (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>)|用來停用或啟用**名稱**和**位置**欄位上**加入新項目** 對話方塊。 值**旗標**欄位是必要的位元旗標的組合十進位對等項目。<br /><br /> 當使用者選取的項目上**新增**索引標籤上，專案會決定是否 [名稱] 欄位和 [位置] 欄位會顯示當**加入新項目**第一次顯示對話方塊。 項目，透過.vsdir 檔案，可以控制只選取項目時是否將欄位會啟用與停用。|  
|SuggestedBaseName|代表檔案、 精靈 」 或範本的預設名稱。 這個欄位是字串或表單"#ResID 」 資源識別項。 IDE 會使用此值來提供項目的預設名稱。 整數值，讓名稱成為唯一的例如 MyFile21.asp 會附加此基底值。<br /><br /> 在上述清單中，描述、 DLLPath、 IconResourceId、 旗標和 SuggestedBaseNumber 僅適用於範本和精靈的檔案。 這些欄位不適用於資料夾中。 這項事實如下所示的 BscPrjProjectItems 檔案中的程式碼\<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems 登錄機碼。 這個檔案包含三筆記錄 （一個用於每個資料夾） 與每一筆記錄的四個欄位： RelPathName，{clsidPackage}，LocalizedName 和 SortPriority。<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120`|  
  
 當您建立精靈檔時，您也應該考慮下列問題。  
  
-   任何有意義的資料是任何非必要的欄位應包含 0 （零），做為預留位置。  
  
-   如果不提供任何當地語系化的名稱，則相對路徑名稱會使用精靈檔案中。  
  
-   DLLPath 會覆寫 clsidPackage 圖示的位置。  
  
-   如果沒有定義圖示，IDE 會替代具有該副檔名的檔案的預設圖示。  
  
-   如果不提供任何建議的基底名稱，則會使用 'Project'。  
  
-   如果您刪除.vsz 檔案、 資料夾或範本檔案，您也必須從.vsdir 檔案中移除其相關聯的記錄。  
  
## <a name="see-also"></a>請參閱  
 [精靈](../../extensibility/internals/wizards.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)