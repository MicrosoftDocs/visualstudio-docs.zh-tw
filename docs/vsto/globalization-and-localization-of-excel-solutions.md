---
title: Excel 方案的全球化與當地語系化
description: 瞭解 Microsoft Office Excel 解決方案的特殊考慮，這些問題將會在具有非英文設定的 Windows 電腦上執行。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fc61f66b2aefaf0e43b1b5af819e0e244feec114
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910314"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Excel 方案的全球化與當地語系化
  本節包含在非英文設定的 Windows 電腦上執行 Microsoft Office Excel 解決方案之特殊考量的相關資訊。 當您使用 Visual Studio 建立其他種類的解決方案時，遇到的 Microsoft Office 解決方案全球化和當地語系化問題層面，大部分都一樣。 如需一般資訊，請參閱 [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)。

 根據預設，在任何 Windows 地區設定中，主控制項都能在 Microsoft Office Excel 中運作正常，只要所有使用 Managed 程式碼傳遞或操作的資料格式都使用英文 (美國) 格式。 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]為目標的專案中，這個行為是由通用語言執行平台 (CLR) 控制。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="format-data-in-excel-with-various-regional-settings"></a>使用不同的地區設定來格式化 Excel 中的資料
 您必須先使用英文 (美國) 資料格式 (地區設定識別碼 1033) 格式化所有區分地區設定格式的資料，例如日期和貨幣，再將它傳遞至 Microsoft Office Excel 或從 Office 專案程式碼讀取資料。

 根據預設，當您在 Visual Studio 中開發 Office 解決方案時，Excel 物件模型預期使用地區設定識別碼 1033 資料格式 (這也稱之為物件模型鎖定為地區設定識別碼 1033)。 這種行為符合 Visual Basic 應用程式的運作方式。 不過，您可以在 Office 解決方案中修改這種行為。

### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>瞭解 Excel 物件模型永遠預期地區設定識別碼1033
 根據預設，您使用 Visual Studio 建立的 Office 解決方案不受使用者地區設定的影響，其行為表現一律如同地區設定是英文 (美國)。 例如，如果在 Excel 中取得或設定 <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> 屬性，資料必須按照地區設定識別碼 1033 預期的方式格式化。 如果使用不同的資料格式，可能得不到預期的結果。

 雖然 Managed 程式碼傳遞或操作的資料使用了英文 (美國) 格式，但 Excel 仍會根據使用者的地區設定正確轉譯和顯示資料。 Excel 能夠正確地格式化資料，是因為 Managed 程式碼會把地區設定識別碼 1033 和資料一起傳遞，這表示資料是英文 (美國) 格式，因此必須重新格式以符合使用者的地區設定。

 例如，如果使用者的地區選項設為德文 (德國) 地區設定，他們會希望 2005 年 6 月 29 日這個日期格式化成：29.06.2005。 不過，如果您的解決方案將日期傳遞至 Excel 做為字串，您就必須根據英文 (美國) 格式將日期格式化成：6/29/2005。 如果儲存格已格式化為 [日期] 儲存格，Excel 就會以德文 (德國) 格式顯示日期。

### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>將其他地區設定識別碼傳遞至 Excel 物件模型
 通用語言執行平台 (CLR) 會自動將地區設定識別碼 1033 傳遞給接受區分地區設定資料之 Excel 物件模型中的所有方法和屬性。 沒有任何方法可以自動為進入物件模型的所有呼叫變更此行為。 但是，您可以將不同的地區設定識別碼傳遞給特定的方法：使用 <xref:System.Type.InvokeMember%2A> 呼叫方法，並把地區設定識別碼傳遞給此方法的 *culture* 參數。

## <a name="localize-document-text"></a>當地語系化檔文字
 專案中的文件、範本或活頁簿可能包含靜態文字，必須從組件和其他 Managed 資源分別予以當地語系化。 最直截了當的方式，是建立一份文件的複本，然後用 Microsoft Office Word 或 Microsoft Office Excel 翻譯文字。 即使不變更程式碼，這個程序都能發揮作用，因為所有文件編號都會連結到相同的組件。

 您仍然必須確定與文件文字互動的任何程式碼部分會繼續符合文字語言，而書籤、命名的範圍和其他顯示欄位會配合 Office 文件對不同文法和文字長度的任何重新格式化進行必要的調整。 對於包含極少量文字的文件範本，您可以考慮將文字儲存在資源檔，然後在執行階段載入文字。

### <a name="text-direction"></a>文字方向
 在 Excel 中，您可以設定工作表屬性呈現由右至左的文字。 裝載在設計工具上的主控制項或任何具有屬性的控制項， `RightToLeft` 會在執行時間自動符合這些設定。 Word 沒有雙向文字的檔設定 (您只要變更文字) 的對齊方式，就不能將控制項對應至此設定。 您必須改為每個控制項設定文字對齊方式。 也可以撰寫程式碼來梳理所有控制項，強制其文字由右至左呈現。

### <a name="change-culture"></a>變更文化特性
 您的文件層級自訂程式碼通常會共用主要的 Excel UI 執行緒，讓您對執行緒文化特性進行的任何變更都會影響在該執行緒上執行的其他所有項目；變更不限於自訂項目。

 Windows Forms 控制項都已先初始化，然後主應用程式才啟動應用程式層級的 VSTO 增益集。 在這些情況下，應該先變更文化特性再設定 UI 控制項。

## <a name="install-the-language-packs"></a>安裝語言套件
 如果您擁有非英文版的 Windows 設定，您可以安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 語言套件，查看與 Windows 相同語言的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 訊息。 如果任何使用者使用非英文設定的 Windows 執行您的解決方案，他們必須有正確的語言套件才能查看與 Windows 相同語言的執行階段訊息。 您 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可以從 [Microsoft 下載中心](https://www.microsoft.com/download)取得語言套件。

 此外，ClickOnce 訊息必須有可轉散發的 .NET Framework 語言套件 。 您可以從 [Microsoft 下載中心](https://www.microsoft.com/download)取得 .NET Framework 語言套件。

## <a name="regional-settings-and-excel-com-calls"></a>地區設定和 Excel COM 呼叫
 只要 Managed 用戶端呼叫 COM 物件上的方法，就需要傳遞特定文化特性的資訊，它使用符合目前執行緒地區設定的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (地區設定) 執行此項作業。 目前執行緒的地區設定預設繼承自使用者的地區設定。 不過，當您從使用 Visual Studio 中的 Office 開發工具建立的 Excel 解決方案呼叫 Excel 物件模型時，英文 (美國) 資料格式 (地區設定識別碼 1033) 就會自動傳遞到 Excel 物件模型。 您必須先使用英文 (美國) 資料格式格式化所有區分地區設定格式的資料，例如日期和貨幣，再將它傳遞至 Microsoft Office Excel 或從您的專案程式碼讀取資料。

## <a name="considerations-for-storing-data"></a>儲存資料的考慮
 為確保正確解譯及顯示資料，您也應該考慮應用程式以字串常值 (硬式編碼) 儲存資料，不用強型別物件時，可能發生的問題，例如 Excel 工作表公式。 您應該使用假設不因文化特性而異或以英文 (美國) (LCID 值 1033) 樣式進行格式化的資料。

### <a name="applications-that-use-string-literals"></a>使用字串常值的應用程式
 可行的值可能是硬式編碼，包括以英文 (美國) 格式撰寫的日期常值，和包含當地語系化函式名稱的 Excel 工作表公式。 另一個可能性可以是包含數字的硬式編碼字串，例如 "1,000"；在某些文化特性中，這會解譯為一千，但在其他文化特性中，它代表一點零。 以錯誤格式執行的計算和比較可能會導致不正確的資料。

 Excel 會根據隨字串傳遞的 LCID 解譯任何字串。 如果字串的格式與傳遞的 LCID 不相應，這可能會發生問題。 使用 Visual Studio 中的 Office 開發工具所建立的 Excel 解決方案，在傳遞所有資料時都使用 LCID 1033 (en-US)。 Excel 會根據地區設定和 Excel 使用者介面語言顯示資料。 Visual Basic for Applications (VBA) 也以這種方式運作，字串格式化為 en-US 且 VBA 幾乎一律依 LCID 傳遞 0 (中性語言)。 例如，下列 VBA 程式碼會根據目前的使用者地區設定，顯示5月 12 2004 日格式正確的值：

```vb
'VBA
Application.ActiveCell.Value2 = "05/12/04"
```

 但相同的程式碼，用在以 Visual Studio 中的 Office 開發工具建立的解決方案並透過 COM Interop 傳遞到 Excel 時，產生的結果和以 en-US 樣式格式化的日期一樣。

 例如：

 [!code-vb[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#6)]
 [!code-csharp[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#6)]

 您應該盡可能使用強型別資料，不要使用字串常值。 例如，不要用字串常值儲存日期，而要儲存為 <xref:System.Double>，然後將它轉換成 <xref:System.DateTime> 物件操作。

 下列程式碼範例採用使用者在儲存格 A5 輸入的日期，儲存為 <xref:System.Double>，然後再轉換成 <xref:System.DateTime> 物件顯示在儲存格 A7 中。 儲存格 A7 必須格式化才能顯示日期。

 [!code-vb[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#7)]
 [!code-csharp[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#7)]

### <a name="excel-worksheet-functions"></a>Excel 工作表函數
 大部分語言的 Excel 版本，工作表函數名稱都是內部轉譯。 不過，由於可能的語言和 COM interop 問題，建議您在程式碼中只使用英文函式名稱。

### <a name="applications-that-use-external-data"></a>使用外部資料的應用程式
 任何開啟或使用外部資料的程式碼，例如包含從舊有系統匯出的以逗號分隔值的檔案 (CSV 檔案)，如果使用 en-US 以外的任何格式匯出，也可能受到影響。 因為所有值應該都是二進位格式，所以資料庫存取可能不受影響；除非資料庫將日期儲存為字串，或執行了不使用二進位格式的作業。 此外，如果您使用 Excel 資料建構 SQL 查詢，您可能需要確保其為 en-US 格式，視所用函數而定。

## <a name="see-also"></a>另請參閱

- [如何：以 Office 多語系使用者介面為目標](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)