---
title: '將自訂的解壓縮規則編碼 (web 效能測試) '
description: 瞭解如何建立您自己的解壓縮規則，衍生自 ExtractionRule 的解壓縮規則類別。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- extraction rules
- Web performance tests, creating custom extraction rules
- extraction rules, creating custom
ms.assetid: 6bcc5712-6cc6-4f59-8933-6e8078318c45
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e03a289ee95e9aefddb49154d1199fffa31ce3ca
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442452"
---
# <a name="code-a-custom-extraction-rule-for-a-web-performance-test"></a>為 Web 效能測試撰寫自訂擷取規則程式碼

您可以建立自己的擷取規則。 若要執行這項操作，可以從擷取規則類別中衍生自己的規則。 擷取規則衍生自 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> 基底類別。

> [!NOTE]
> 您也可以建立自訂驗證規則。 如需詳細資訊，請參閱[為負載測試建立自訂程式碼和外掛程式](../test/create-custom-code-and-plug-ins-for-load-tests.md)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-extraction-rule"></a>若要建立自訂擷取規則

1. 開啟包含 Web 效能測試的測試專案。

2. (選擇性) 建立個別的類別庫專案，以存放擷取規則。

    > [!IMPORTANT]
    > 您可以在測試所在的同一個專案中建立類別。 不過，如果要重複使用規則，最好是建立個別的類別庫專案，以存放規則。 如果您要建立個別的專案，必須完成本程序中的選擇性步驟。

3. (選擇性) 在類別庫專案中，加入 Microsoft.VisualStudio.QualityTools.WebTestFramework dll 的參考。

4. 建立從 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> 類別衍生的類別。 實作<xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> 和 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*> 成員。

5. (選擇性) 建立新的「類別庫」專案。

6. (選擇性) 在測試專案中，新增包含自訂擷取規則的類別庫專案參考。

7. 在測試專案中，開啟 **Web 效能測試編輯器** 中的 web 效能測試。

8. 若要新增自訂擷取規則，請以滑鼠右鍵按一下 Web 效能測試要求，然後選取 [新增擷取規則]。

     [新增擷取規則] 對話方塊隨即出現。 您會在 [選取規則] 清單中看到您的自訂驗證規則，以及預先定義的驗證規則。 選取自訂擷取規則，然後選擇 [確定]。

9. 執行您的 Web 效能測試。

## <a name="example"></a>範例

下列程式碼顯示自訂擷取規則的實作。 這個擷取規則會從指定的輸入欄位中擷取值。 可以使用這個範例做為您自訂擷取規則的起點。

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.TestTools.WebTesting;
using System.Globalization;

namespace ClassLibrary2
{
    //-------------------------------------------------------------------------
    // This class creates a custom extraction rule named "Custom Extract Input"
    // The user of the rule specifies the name of an input field, and the
    // rule attempts to extract the value of that input field.
    //-------------------------------------------------------------------------
    public class CustomExtractInput : ExtractionRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Extract Input"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Extracts the value from a specified input field"; }
        }

        // The name of the desired input field
        private string NameValue;
        public string Name
        {
            get { return NameValue; }
            set { NameValue = value; }
        }

        // The Extract method.  The parameter e contains the web performance test context.
        //---------------------------------------------------------------------
        public override void Extract(object sender, ExtractionEventArgs e)
        {
            if (e.Response.HtmlDocument != null)
            {
                foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(new string[] { "input" }))
                {
                    if (String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase))
                    {
                        string formFieldValue = tag.GetAttributeValueAsString("value");
                        if (formFieldValue == null)
                        {
                            formFieldValue = String.Empty;
                        }

                        // add the extracted value to the web performance test context
                        e.WebTest.Context.Add(this.ContextParameterName, formFieldValue);
                        e.Success = true;
                        return;
                    }
                }
            }
            // If the extraction fails, set the error text that the user sees
            e.Success = false;
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name);
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports Microsoft.VisualStudio.TestTools.WebTesting
Imports System.Globalization

Namespace ClassLibrary2

    '-------------------------------------------------------------------------
    ' This class creates a custom extraction rule named "Custom Extract Input"
    ' The user of the rule specifies the name of an input field, and the
    ' rule attempts to extract the value of that input field.
    '-------------------------------------------------------------------------
    Public Class CustomExtractInput
        Inherits ExtractionRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Extract Input"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Extracts the value from a specified input field"
            End Get
        End Property

        ' The name of the desired input field
        Private NameValue As String
        Public Property Name() As String
            Get
                Return NameValue
            End Get
            Set(ByVal value As String)
                NameValue = value
            End Set
        End Property

        ' The Extract method.  The parameter e contains the web performance test context.
        '---------------------------------------------------------------------
        Public Overrides Sub Extract(ByVal sender As Object, ByVal e As ExtractionEventArgs)

            If Not e.Response.HtmlDocument Is Nothing Then

                For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(New String() {"input"})

                    If String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase) Then

                        Dim formFieldValue As String = tag.GetAttributeValueAsString("value")
                        If formFieldValue Is Nothing Then

                            formFieldValue = String.Empty
                        End If

                        ' add the extracted value to the web performance test context
                        e.WebTest.Context.Add(Me.ContextParameterName, formFieldValue)
                        e.Success = True
                        Return
                    End If
                Next
            End If
            ' If the extraction fails, set the error text that the user sees
            e.Success = False
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name)
        End Sub
    End Class
End Namespace
```

<xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> 方法包含擷取規則的核心功能。 之前範例中的 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> 方法可接受 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs> (其提供此擷取規則涵蓋的要求所產生之回應)。 回應中含有 <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument>，後者又含有回應中的所有標籤。 輸出標籤會從 <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> 中篩選掉。 每個輸入標記都會受到檢查，看其中是否有稱為 `name` 的屬性 (attribute)，其值與使用者提供的 `Name` 屬性 (property) 值相同。 如果找到屬性相符的標記，就會試著擷取 `value` 屬性 (如果存在) 所含的值。 如果這個屬性存在，就會擷取標籤的名稱和值，然後加入至 Web 效能測試內容中。 此擷取規則通過。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHttpHeader>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractRegularExpression>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHiddenFields>
- [為 Web 效能測試撰寫自訂驗證規則程式碼](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
