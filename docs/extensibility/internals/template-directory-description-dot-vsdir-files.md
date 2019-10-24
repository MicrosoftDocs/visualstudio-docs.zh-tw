---
title: 範本目錄描述（。Vsdir）檔案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb20a1fbc8d5edd9783521fa933dbddc74ac2a22
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722819"
---
# <a name="template-directory-description-vsdir-files"></a>範本目錄描述檔 (.Vsdir)
範本目錄描述檔（vsdir）是一個文字檔，可讓整合式開發環境（IDE）顯示資料夾、wizard .vsz 檔案，以及與您在對話方塊中的專案相關聯的範本檔案。 內容包含每個檔案或資料夾的一筆記錄。 雖然通常只會提供一個 vsdir 檔案來描述多個資料夾、嚮導或範本檔案，但會合並參考位置中的所有 vsdir 檔案。

 資料夾（子目錄）、vsdir 檔案中所參考的檔案，以及該檔案本身的檔案，全都位於相同的目錄中。 當 IDE 執行嚮導或在 [**新增專案**] 或 [**加入新專案**] 對話方塊中顯示資料夾或檔案時，ide 會檢查包含已執行檔案的目錄，以判斷是否有一個 vsdir 檔案。 如果找到一個 vsdir 檔案，IDE 就會讀取它，以判斷它是否包含已執行或已顯示之資料夾或檔案的專案。 如果找到專案，IDE 會使用執行嚮導或顯示內容中的資訊。

 下列程式碼範例來自 \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files 登錄機碼中的 file SourceFiles：

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 在此情況下，兩個記錄會在一個檔案中。 換行（回車符）會分隔每一筆記錄。 每一行代表不同的檔案類型。 分隔號（&#124;）字元會分隔每一筆記錄中的欄位。 單一目錄可以包含多個具有不同檔案名的 vsdir 檔案，或者每個檔案類型都可以有一個 vsdir 檔案。

## <a name="fields"></a>欄位
 下表列出為每一筆記錄指定的欄位。

| 欄位 | 描述 |
| - | - |
| 相對路徑名稱（RelPathName） | 資料夾、範本或 .vsz 檔案的名稱，例如 HeaderFile 或 MyWizard。 此欄位也可以是用來表示資料夾的名稱。 |
| {clsidPackage} | VSPackage 的 GUID，可讓您存取 VSPackage 的附屬動態連結程式庫（DLL）資源中的當地語系化字串，例如 LocalizedName、Description、IconResourceId 和 SuggestedBaseName。 如果未提供 DLLPath，則會套用 IconResourceId。 **注意：** 除非一個或多個先前的欄位是資源識別碼，否則此欄位是選擇性的。 此欄位通常是空白，適用于與不將其文字當地語系化的協力廠商嚮導對應的檔案。 |
| LocalizedName | 範本檔案或 wizard 的當地語系化名稱。 此欄位可以是字串或格式為 "#ResID" 的資源識別碼。 這個名稱會顯示在 [**加入新專案**] 對話方塊中。 **注意：** 如果 LocalizedName 是資源識別碼，則需要 {clsidPackage}。 |
| SortPriority | 整數，代表此範本檔案或 wizard 的相對優先順序。 例如，如果此專案的值為1，則此專案會顯示在 [其他專案] 旁，其值為1，而 [所有專案] 的排序值為2或更大。<br /><br /> 排序優先順序相對於相同目錄中的專案。 同一個目錄中可能有多個 vsdir 檔案。 在這種情況下，就是所有的專案<em>。</em>會合並該目錄中的 vsdir 檔案。 具有相同優先權的專案會以顯示名稱不區分大小寫的詞典編纂順序列出。 @No__t_0 函數是用來排序專案。<br /><br /> 不是在 vsdir 檔案中描述的專案，其優先順序數位會大於此 vsdir 檔案中所列的最高優先順序數位。 結果是這些專案是在顯示清單的結尾，不論其名稱為何。 |
| 描述 | 範本檔案或 wizard 的當地語系化描述。 此欄位可以是字串或格式為 "#ResID" 的資源識別碼。 選取專案時，這個字串會出現在 [**新增專案**] 或 [**加入新專案**] 對話方塊中。 |
| DLLPath 或 {clsidPackage} | 用來載入範本檔案或 wizard 的圖示。 圖示會使用 IconResourceId，以資源的形式載入 .dll 或 .exe 檔案。 您可以使用完整路徑或使用 VSPackage 的 GUID 來識別這個 .dll 或 .exe 檔案。 VSPackage 的執行 DLL 是用來載入圖示（而不是附屬 DLL）。 |
| IconResourceId | DLL 或 VSPackage 執行 DLL 中的資源識別碼，可決定要顯示的圖示。 |
| 旗標（<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>） | 用來停用或啟用 [**加入新專案**] 對話方塊上的 [**名稱**] 和 [**位置**] 欄位。 [**旗標**] 欄位的值是所需的位旗標之組合的十進位對應項。<br /><br /> 當使用者在 [**新增**] 索引標籤上選取專案時，專案會決定在第一次顯示 [**加入新專案**] 對話方塊時，是否要顯示 [名稱] 欄位和 [位置] 欄位。 透過 vsdir 檔案的專案，只能控制當選取專案時，欄位是否啟用與停用。 |
| SuggestedBaseName | 表示檔案、wizard 或範本的預設名稱。 此欄位可以是字串或 "#ResID" 格式的資源識別碼。 IDE 會使用此值來提供專案的預設名稱。 此基底值會附加一個整數值，使其成為唯一的名稱，例如 MyFile21。<br /><br /> 在先前的清單中，Description、DLLPath、IconResourceId、Flags 和 SuggestedBaseNumber 僅適用于範本和 wizard 檔案。 這些欄位不適用於資料夾。 此事實會在 \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems 登錄機碼中 BscPrjProjectItems 檔案的程式碼中說明。 此檔案包含三個記錄（每個資料夾各一個），每筆記錄都有四個欄位： RelPathName、{clsidPackage}、LocalizedName 和 SortPriority。<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 當您建立 wizard 檔案時，您也應該考慮下列問題。

- 沒有有意義之資料的任何非必要欄位，都應該包含0（零）做為預留位置。

- 如果未提供當地語系化的名稱，則會在 wizard 檔案中使用相對路徑名稱。

- DLLPath 會覆寫圖示位置的 clsidPackage。

- 如果未定義任何圖示，IDE 會替代具有該副檔名之檔案的預設圖示。

- 如果未提供建議的基底名稱，則會使用 ' Project '。

- 如果刪除 .vsz 檔案、資料夾或範本檔案，您也必須從該檔案中移除其相關聯的記錄。

## <a name="see-also"></a>請參閱
- [精靈](../../extensibility/internals/wizards.md)
- [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)