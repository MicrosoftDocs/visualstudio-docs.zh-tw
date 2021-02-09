---
title: 範本目錄描述 (。Vsdir) 檔案 |Microsoft Docs
description: 瞭解範本目錄描述檔案如何讓 Visual Studio IDE 顯示資料夾、.vsz 檔案，以及與您的專案相關聯的範本。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0e2b56c061ce6e3124a7ed5a5dc00e41c3964204
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898252"
---
# <a name="template-directory-description-vsdir-files"></a>範本目錄描述檔 (.Vsdir)
範本目錄描述檔 ( 的) 是一個文字檔，可讓整合式開發環境 (IDE) ，在對話方塊中顯示與專案相關聯的資料夾、wizard .vsz 檔案和範本檔案。 每個檔案或資料夾的內容都包含一筆記錄。 雖然通常只會提供一個 vsdir 檔案來描述多個資料夾、嚮導或範本檔案，但會合並參考位置中的所有 vsdir 檔案。

 資料夾 (子目錄) 、vsdir 檔中所參考的檔案，以及該檔案本身全都位於相同的目錄中。 當 IDE 執行 wizard 或在 [ **新增專案** ] 或 [ **加入新** 專案] 對話方塊中顯示資料夾或檔案時，IDE 會檢查包含已執行檔案的目錄，以判斷是否存在一個 vsdir 檔案。 如果找到一個 vsdir 檔案，IDE 會將它讀取，以判斷它是否包含已執行或已顯示之資料夾或檔案的專案。 如果找到某個專案，IDE 會使用執行嚮導或顯示內容的資訊。

 下列程式碼範例來自 \Bscprj\bscprj\bscprjprojectitems\ Source_Files 登錄機碼中的 file SourceFiles \<EnvSDK> ：

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 在此情況下，有兩筆記錄在一個檔案中。 分行符號 (換行字元) 分隔每一筆記錄。 每一行都代表不同的檔案類型。 管道 ( # A0) 字元會分隔每一筆記錄中的欄位。 單一目錄可以包含多個檔案名不同的檔案，或者每個檔案類型可以有一個 vsdir 檔案。

## <a name="fields"></a>欄位
 下表列出為每筆記錄指定的欄位。

| 欄位 | 描述 |
| - | - |
| RelPathName) 的相對路徑名稱 ( | 資料夾、範本或 .vsz 檔案的名稱，例如 HeaderFile .h 或 MyWizard。 這個欄位也可以是用來表示資料夾的名稱。 |
| {clsidPackage} | VSPackage 的 GUID，可在 VSPackage 的附屬動態連結程式庫中存取當地語系化的字串，例如 LocalizedName、Description、IconResourceId 和 SuggestedBaseName， (DLL) 資源。 如果未提供 DLLPath，則適用 IconResourceId。 **注意：**  除非先前的一或多個欄位是資源識別碼，否則這個欄位是選擇性欄位。 這個欄位通常是空白的，也就是與協力廠商的程式（不會當地語系化其文字）相對應的檔。 |
| LocalizedName | 範本檔案或 wizard 的當地語系化名稱。 這個欄位可以是字串或 "#ResID" 格式的資源識別碼。 這個名稱會顯示在 [ **加入新專案** ] 對話方塊中。 **注意：**  如果 LocalizedName 是資源識別碼，則需要 {clsidPackage}。 |
| SortPriority | 整數，代表這個範本檔或 wizard 的相對優先權。 例如，如果這個專案的值為1，則此專案會顯示在值為1的其他專案旁邊，以及排序值為2或更大的所有專案的前面。<br /><br /> 排序優先順序是相對於相同目錄中的專案。 相同的目錄中可能會有一個以上的 vsdir 檔案。 在這種情況下，就是來自所有的專案 <em>。</em>該目錄中的 vsdir 檔案會合並。 具有相同優先權的專案會以不區分大小寫的詞典編纂順序列出顯示的名稱。 `_wcsicmp`函數是用來排序專案。<br /><br /> 在 vsdir 檔中未描述的專案，其優先順序數位會大於在 vsdir 檔案中列出的最高優先順序號碼。 結果是這些專案在顯示清單的結尾，不論其名稱為何。 |
| Description | 範本檔案或 wizard 的當地語系化描述。 這個欄位可以是字串或 "#ResID" 格式的資源識別碼。 選取專案時，這個字串會出現在 [ **新增專案** ] 或 [ **加入新專案** ] 對話方塊中。 |
| DLLPath 或 {clsidPackage} | 用來載入範本檔案或 wizard 的圖示。 此圖示會使用 IconResourceId，從 .dll 或 .exe 檔案載入為資源。 您可以使用完整路徑或使用 VSPackage 的 GUID 來識別這個 .dll 或 .exe 檔案。 VSPackage 的「執行」 DLL 可用來載入 (非附屬 DLL) 的圖示。 |
| IconResourceId | DLL 或 VSPackage 執行 DLL 中的資源識別碼，可決定要顯示的圖示。 |
| 旗標 (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>)  | 用來停用或啟用 [**加入新專案**] 對話方塊上的 [**名稱**] 和 [**位置**] 欄位。 [ **旗標** ] 欄位的值是必要位旗標組合的十進位對等專案。<br /><br /> 當使用者選取 [ **新增** ] 索引標籤上的專案時，專案會決定當第一次顯示 [ **加入新專案** ] 對話方塊時，是否顯示 [名稱] 欄位和 [位置] 欄位。 專案（透過一個 vsdir 檔案）只能控制選取專案時是否啟用和停用欄位。 |
| SuggestedBaseName | 代表檔案、wizard 或範本的預設名稱。 此欄位可能是字串或 "#ResID" 格式的資源識別碼。 IDE 會使用此值來提供專案的預設名稱。 這個基底值會附加一個整數值，讓名稱成為唯一的，例如 MyFile21. asp。<br /><br /> 在先前的清單中，Description、DLLPath、IconResourceId、Flags 和 SuggestedBaseNumber 只適用于範本和 wizard 檔案。 這些欄位不適用於資料夾。 這項事實說明于 \BscPrj\BscPrj\BscPrjProjectItems 登錄機碼中 BscPrjProjectItems 檔案的程式碼中 \<EnvSDK> 。 此檔案包含三個 (記錄，每個資料夾) 有四個欄位，每一筆記錄有四個欄位： RelPathName、{clsidPackage}、LocalizedName 和 SortPriority。<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 當您建立 wizard 檔案時，您也應該考慮下列問題。

- 任何沒有有意義資料的非必要欄位都應該包含 0 (零) 作為預留位置。

- 如果未提供當地語系化名稱，則會在嚮導檔案中使用相對路徑名稱。

- DLLPath 會覆寫圖示位置的 clsidPackage。

- 如果未定義任何圖示，IDE 會以預設圖示取代具有該副檔名的檔案。

- 如果未提供建議的基底名稱，則會使用 ' Project '。

- 如果您刪除 .vsz 檔案、資料夾或範本檔案，您也必須從該 vsdir 檔中移除其相關聯的記錄。

## <a name="see-also"></a>另請參閱
- [精靈](../../extensibility/internals/wizards.md)
- [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
