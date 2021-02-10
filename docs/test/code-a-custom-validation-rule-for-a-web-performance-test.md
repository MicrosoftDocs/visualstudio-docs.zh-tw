---
title: 建立 web 效能測試的自訂驗證規則
description: 瞭解如何建立您自己的驗證規則，衍生自驗證規則類別（ValidationRule）。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- custom validation rules
- validation rules, creating
- web performance tests, creating custom validation rules
- rules, validation
- validation rules
ms.assetid: 989124bc-1a86-41f7-b37d-8f9e54dd4f0b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: ae5228c4da9abef9b5bee417d5d3d71bb28d416d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964585"
---
# <a name="code-a-custom-validation-rule-for-a-web-performance-test"></a>為 Web 效能測試撰寫自訂驗證規則程式碼

您可以建立自己的驗證規則。 若要執行這項作業，您可以從驗證規則類別中衍生自己的規則類別。 驗證規則衍生自 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> 基底類別。

> [!NOTE]
> 您也可以建立自訂擷取規則。 如需詳細資訊，請參閱[為負載測試建立自訂程式碼和外掛程式](../test/create-custom-code-and-plug-ins-for-load-tests.md)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-custom-validation-rules"></a>若要建立自訂驗證規則

1. 開啟包含 Web 效能測試的測試專案。

2. (選擇性) 建立個別的類別庫專案，以存放驗證規則。

    > [!IMPORTANT]
    > 您可以在測試所在的同一個專案中建立類別。 不過，如果要重複使用規則，最好是建立個別的類別庫專案，以存放規則。 如果您要建立個別的專案，必須完成本程序中的選擇性步驟。

3. (選擇性) 在「類別庫」專案中，加入 Microsoft.VisualStudio.QualityTools.WebTestFramework DLL 的參考。

4. 建立從 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> 類別衍生的類別。 實作<xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.Validate*> 和 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.RuleName*> 成員。

5. (選擇性) 建立新的「類別庫」專案。

6. (選擇性) 在測試專案中，加入包含自訂驗證規則之類別庫專案的參考。

7. 在測試專案中，開啟 **Web 效能測試編輯器** 中的 web 效能測試。

8. 若要將自訂驗證規則加入至 web 效能測試要求，請以滑鼠右鍵按一下要求，然後選取 [ **加入驗證規則**]。

     [新增驗證規則] 對話方塊隨即出現。 您會在 [選取規則] 清單中看到您的自訂驗證規則，以及預先定義的驗證規則。 選取您的自訂驗證規則，然後選擇 [確定]。

9. 執行您的 Web 效能測試。

## <a name="example"></a>範例

下列程式碼顯示自訂驗證規則的實作。 這個驗證規則會模擬預先定義之「必要標記」驗證規則的行為。 可以使用這個範例做為您自訂驗證規則的起點。

> [!WARNING]
> 自訂驗證器之程式碼中的公用屬性不可有 null 值。

```csharp
using System;
using System.Diagnostics;
using System.Globalization;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleWebTestRules
{
    //-------------------------------------------------------------------------
    // This class creates a custom validation rule named "Custom Validate Tag"
    // The custom validation rule is used to check that an HTML tag with a
    // particular name is found one or more times in the HTML response.
    // The user of the rule can specify the HTML tag to look for, and the
    // number of times that it must appear in the response.
    //-------------------------------------------------------------------------
    public class CustomValidateTag : ValidationRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Validate Tag"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Validates that the specified tag exists on the page."; }
        }

        // The name of the required tag
        private string RequiredTagNameValue;
        public string RequiredTagName
        {
            get { return RequiredTagNameValue; }
            set { RequiredTagNameValue = value; }
        }

        // The minimum number of times the tag must appear in the response
        private int MinOccurrencesValue;
        public int MinOccurrences
        {
            get { return MinOccurrencesValue; }
            set { MinOccurrencesValue = value; }
        }

        // Validate is called with the test case Context and the request context.
        // These allow the rule to examine both the request and the response.
        //---------------------------------------------------------------------
        public override void Validate(object sender, ValidationEventArgs e)
        {
            bool validated = false;
            int numTagsFound = 0;

            foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName))
            {
                Debug.Assert(string.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase));

                if (++numTagsFound >= MinOccurrences)
                {
                    validated = true;
                    break;
                }
            }

            e.IsValid = validated;

            // If the validation fails, set the error text that the user sees
            if (!validated)
            {
                if (numTagsFound > 0)
                {
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound);
                }
                else
                {
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName);
                }
            }
        }
    }
}
```

```vb
Imports System
Imports System.Diagnostics
Imports System.Globalization
Imports Microsoft.VisualStudio.TestTools.WebTesting

Namespace SampleWebTestRules

    '-------------------------------------------------------------------------
    ' This class creates a custom validation rule named "Custom Validate Tag"
    ' The custom validation rule is used to check that an HTML tag with a
    ' particular name is found one or more times in the HTML response.
    ' The user of the rule can specify the HTML tag to look for, and the
    ' number of times that it must appear in the response.
    '-------------------------------------------------------------------------
    Public Class CustomValidateTag
        Inherits Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Validate Tag"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Validates that the specified tag exists on the page."
            End Get
        End Property

        ' The name of the required tag
        Private RequiredTagNameValue As String
        Public Property RequiredTagName() As String
            Get
                Return RequiredTagNameValue
            End Get
            Set(ByVal value As String)
                RequiredTagNameValue = value
            End Set
        End Property

        ' The minimum number of times the tag must appear in the response
        Private MinOccurrencesValue As Integer
        Public Property MinOccurrences() As Integer
            Get
                Return MinOccurrencesValue
            End Get
            Set(ByVal value As Integer)
                MinOccurrencesValue = value
            End Set
        End Property

        ' Validate is called with the test case Context and the request context.
        ' These allow the rule to examine both the request and the response.
        '---------------------------------------------------------------------
        Public Overrides Sub Validate(ByVal sender As Object, ByVal e As ValidationEventArgs)

            Dim validated As Boolean = False
            Dim numTagsFound As Integer = 0

            For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName)

                Debug.Assert(String.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase))

                numTagsFound += 1
                If numTagsFound >= MinOccurrences Then

                    validated = True
                    Exit For
                End If
            Next

            e.IsValid = validated

            ' If the validation fails, set the error text that the user sees
            If Not (validated) Then
                If numTagsFound > 0 Then
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound)
                Else
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName)
                End If
            End If
        End Sub
    End Class
End Namespace
```

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidateFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleFindText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequestTime>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredTag>
- [為 Web 效能測試撰寫自訂擷取規則程式碼](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
