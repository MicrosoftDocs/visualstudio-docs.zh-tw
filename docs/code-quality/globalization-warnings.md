---
title: 全球化警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b61b0f10e4231ce1970a55cf352490cbf02a42d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936677"
---
# <a name="globalization-warnings"></a>全球化警告
全球化警告支援全球化程式庫和應用程式。

## <a name="in-this-section"></a>本節內容

|規則|描述|
|----------|-----------------|
|[CA1300:必須指定 MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md)|若要對使用由右至左讀取順序的文化特性 (Culture) 正確顯示訊息方塊，MessageBoxOptions 列舉類型的 RightAlign 和 RtlReading 成員必須傳遞至 Show 方法。|
|[CA1301:避免重複的快速鍵](../code-quality/ca1301-avoid-duplicate-accelerators.md)|便捷鍵也稱為快速鍵，可讓鍵盤使用 ALT 鍵存取控制項。 當多個控制項有重複的便捷鍵時，存取金鑰的行為並未正確定義。|
|[CA1302:請勿地區設定特定的字串](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|System.Environment.SpecialFolder 列舉 (Enumeration) 包含參考特殊系統資料夾的成員。 這些資料夾的位置在不同的作業系統上可有不同的值，使用者可以變更某些位置，而且位置會當地語系化。 Environment.GetFolderPath 方法會傳回與 Environment.SpecialFolder 列舉型別，當地語系化的且適用於目前正在執行的電腦相關聯的位置。|
|[CA1303:不要將常值傳遞做為當地語系化的參數](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|外部可見的方法傳遞字串常值做為參數的建構函式或方法在.NET Framework 類別庫中，且該字串應該是可當地語系化。|
|[CA1304:指定 CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)|方法或建構函式會呼叫具有接受 System.Globalization.CultureInfo 參數之多載的成員，且方法或建構函式未呼叫採用 CultureInfo 參數的多載。 未提供 CultureInfo 或 System.IFormatProvider 物件時，多載成員所提供的預設值可能不會有您希望在所有地區設定中都有的效果。|
|[CA1305:指定 IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)|方法或建構函式所呼叫的一個或多個成員具有可接受 System.IFormatProvider 參數的多載，但該方法或建構函式並未呼叫可接受 IFormatProvider 參數的多載。 未提供 System.Globalization.CultureInfo 或 IFormatProvider 物件時，多載成員所提供的預設值可能不會有您希望在所有地區設定中都有的效果。|
|[CA1306:設定地區設定資料類型](../code-quality/ca1306-set-locale-for-data-types.md)|地區設定會決定資料的文化特性特定展示項目，例如用於數值、貨幣符號和排序次序的格式。 當您建立 DataTable 或 DataSet 時，您應該明確設定地區設定。|
|[CA1307:指定 StringComparison](../code-quality/ca1307-specify-stringcomparison.md)|字串比較作業會使用未設定 StringComparison 參數的方法多載。|
|[CA1308： 必須將字串標準化為大寫字母](../code-quality/ca1308-normalize-strings-to-uppercase.md)|字串應該標準化為大寫字母。 當一小組的字元轉換成小寫字母時，它們無法構成來回行程。|
|[CA1309:使用循序的 StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)|非語言的字串比較作業未將 StringComparison 參數設定為 Ordinal 或 OrdinalIgnoreCase。 藉由明確地將參數設定為 StringComparison.Ordinal 或 StringComparison.OrdinalIgnoreCase，您的程式碼通常可以提升速度、更為正確，也更加可靠。|
|[CA2101： 必須指定的 P/Invoke 字串引數封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|平台叫用成員允許部分信任呼叫端，具有字串參數，並不會不明確封送處理字串。 這樣會造成安全性弱點。|