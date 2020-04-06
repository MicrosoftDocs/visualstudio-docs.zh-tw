---
title: 樣本目錄描述 (.Vsdir) 檔案 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16ba609d5b05d565a12b38bd19e9a777851ced5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704694"
---
# <a name="template-directory-description-vsdir-files"></a>範本目錄描述檔 (.Vsdir)
樣本目錄描述檔 (.vsdir) 是一個文字檔,使整合式開發環境 (IDE) 能夠在對話框中顯示與專案關聯的資料夾、精靈 .vsz 檔案和範本檔。 內容包括每個檔或資料夾的一條記錄。 引用位置中的所有 .vsdir 檔都將合併,儘管通常只提供一個 .vsdir 檔案來描述多個資料夾、嚮導或範本檔。

 資料夾(子目錄)、在 .vsdir 檔中引用的檔案和 .vsdir 檔案本身都位於同一目錄中。 當 IDE 執行精靈或在 **「新專案**」或 **「新增新專案」** 對話框中顯示資料夾或檔時,IDE 將檢查包含已執行檔的目錄,以確定是否存在 .vsdir 檔。 如果找到 .vsdir 檔,IDE 會讀取該檔以確定它是否包含已執行或顯示的資料夾或檔的項目。 如果找到項目,IDE將使用資訊執行精靈或顯示內容。

 以下代碼範例來自\<envSDK>_BscPrj_BscPrj_BscPrjProjectItem_Source_Files注册表项中的文件 SourceFiles.vsdir:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 在這種情況下,兩個記錄位於一個檔中。 新行(回車符)分隔每個記錄。 每行表示不同的文件類型。 管道(&#124;)字元分隔每個記錄中的欄位。 單個目錄可以包含多個具有不同檔名的 .vsdir 檔,也可以為每個檔案類型具有一個 .vsdir 檔。

## <a name="fields"></a>欄位
 下表列出了為每個記錄指定的欄位。

| 欄位 | 描述 |
| - | - |
| 相對路徑名稱(RelPath 名稱) | 資料夾、範本或 .vsz 檔案的名稱,如 headerfile.h 或 MyWizard.vsz。 此字段也可以是用於表示資料夾的名稱。 |
| [clsid 包] | VSPackage 的 GUID,用於在 VSPackage 的衛星動態連結庫 (DLL) 資源中存取本地化字串,如當地語系化名稱、描述、圖示資源 Id 和建議的 BaseName。 如果未提供 DLLPath,則應用圖示資源 Id。 **註:** 此欄位是可選的,除非前面的一個或多個字段是資源標識符。 此欄位對於與不當地語系化其文字的第三方向導對應的第三方向導對應的 .vsdir 檔通常為空。 |
| 本地化名稱 | 樣本檔或嚮導的當地語系化名稱。 此欄位可以是表單「#ResID」的字串或資源標識碼。 此名稱顯示在「**新增新項目」** 對話框中。 **註:** 如果本地化名稱是資源標識符,則需要 [clsid 包]。 |
| 排序優先權 | 表示此範本檔或嚮導的相對優先順序的整數。 例如,如果此項的值為 1,則此項將顯示在值為 1 的其他項旁邊,並領先於排序值為 2 或更大的所有項。<br /><br /> 排序優先順序相對於同一目錄中的項。 同一目錄中可能有多個 .vsdir 檔。 在這種情況下,所有中的項目<em>。</em>該目錄中的 vsdir 檔將合併。 具有相同優先順序的項目按顯示名稱的區分大小寫的詞典順序出。 該`_wcsicmp`函數用於對項目進行排序。<br /><br /> .vsdir 檔中未描述的項包括大於 .vsdir 檔中列出的最大優先順序編號的優先順序編號。 結果是這些項目位於顯示清單的末尾,而不考慮其名稱。 |
| 描述 | 樣本檔或嚮導的本地化說明。 此欄位可以是表單「#ResID」的字串或資源標識碼。 選取**項目**時,此字串將顯示在新**專案或「添加新項目**」對話框中。 |
| DLLPath 或 [clsid 套件] | 用於載入範本檔或嚮導的圖示。 使用 IconResourceId 將圖示載入為 .dll 或 .exe 檔案中的資源。 此 .dll 或 .exe 檔案可以通過使用完整路徑或使用 VSPackage 的 GUID 進行標識。 VSPackage 的實現 DLL 用於載入圖示(而不是衛星 DLL)。 |
| 圖示資源 Id | DLL 或 VSPackage 實現 DLL 中的資源識別碼,用於確定要顯示的圖示。 |
| 標誌<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>( ) | 用於關閉或啟用**新增項目**對話框上的 **「名稱**」 和**位置**欄位。 **"標誌"** 欄位的值是所需位標誌組合的十進制等效項。<br /><br /> 當使用者在 **「新建」** 選項卡上選擇專案時,專案將確定在首次顯示「**添加新專案」** 對話框時是否顯示「名稱」欄位和「位置」欄位。 通過 .vsdir 檔案的專案只能控制欄位是否啟用,在選擇專案時是否禁用。 |
| 建議的基本名稱 | 表示檔、嚮導或範本的預設名稱。 此欄位是表單「#ResID」的字串或資源標識碼。 IDE 使用此值為項提供預設名稱。 此基值附加了整數值,以使名稱唯一,例如MyFile21.asp。<br /><br /> 在上一個清單中,描述、DLLPath、圖示資源Id、標誌和建議BaseNumber僅適用於範本和嚮導檔。 這些欄位不適用於資料夾。 這一事實在\<EnvSDK>_BscPrj_BscPrj_BscPrjProjectItems 註冊表項中的 BscPrjProjectItems 檔中的代碼中進行了說明。 此檔包含三個記錄(每個資料夾一個),每個記錄有四個字段:RelPathName、[clsidPackage]、當地語系化名稱和排序優先順序。<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 創建嚮導檔時,還應考慮以下問題。

- 任何沒有有意義的數據的非必需欄位都應包含 0(零)作為占位元。

- 如果未提供當地語系化名稱,則嚮導檔中將使用相對路徑名稱。

- DLLPath 覆蓋圖示位置的 clsid 包。

- 如果未定義圖示,IDE 將預設圖示替換為具有該擴展名的檔。

- 如果未提供建議的基本名稱,則使用"專案"。

- 如果刪除 .vsz 檔案、資料夾或範本檔,還必須從 .vsdir 檔中刪除其關聯的記錄。

## <a name="see-also"></a>另請參閱
- [嚮導](../../extensibility/internals/wizards.md)
- [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
