---
title: 逐步解說： 使用 XSLT IntelliSense |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5a5a773b17d5393d15a4eb9a5947fe1e3215d784
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486280"
---
# <a name="walkthrough-using-xslt-intellisense"></a>逐步解說：使用 XSLT IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[逐步解說： 使用 XSLT IntelliSense](https://docs.microsoft.com/visualstudio/xml-tools/walkthrough-using-xslt-intellisense)。  
  
  
本逐步解說示範如何使用 XSLT IntelliSense 自動填入某些屬性的值。  
  
### <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>在 xsl:with-param 和 xsl:call-template 項目的名稱屬性中使用 IntelliSense  
  
1.  建立新的 XSLT 檔案，並複製下列程式碼：  
  
    ```  
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
    <!-- These 2 elements effectively assign  
         $messages = resources/en.xml/<messages>,  
         then $messages is used in the "localized-message" template.  -->  
    <xsl:param name="lang">en</xsl:param>  
    <xsl:variable name="messages"  
          select="document(concat('resources/', $lang, '.xml'))/messages"/>   
  
    <xsl:template name="msg23" match="msg23">  
    </xsl:template>  
  
    <xsl:template name="localized-message">  
      <xsl:param name="msgcode"/>  
      <!-- Show message string. -->  
      <xsl:message terminate="yes">  
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>  
      </xsl:message>  
    </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
2.  在 `<xsl:template name="msg23" match="msg23">` 之後插入資料指標並按 ENTER。 接著開始輸入下列 `xsl:call-template` 項目：  
  
    ```  
    <xsl:call-template name="localized-message">  
    </xsl:call-template>  
    ```  
  
     當您輸入時，範本名稱的清單會出現在 `name=""` 項目的 `xsl:call-template` 屬性中。  
  
3.  在 `<xsl:call-template name="localized-message">` 之後插入資料指標並按 ENTER。 接著開始輸入下列 `xsl:with-param` 項目：  
  
    ```  
    <xsl:with-param name="msgcode">msg23</xsl:with-param>  
    ```  
  
     參數名稱的清單會出現在 `name=""` 項目的 `xsl:with-param` 屬性中。  
  
### <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>在 xsl:apply-templates 項目的模式屬性中使用 IntelliSense  
  
1.  建立新的 XSLT 檔案，並複製下列程式碼：  
  
    ```  
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
      <xsl:template match="/">  
        <HTML>  
          <BODY>  
            <TABLE>  
              <xsl:apply-templates select="customers/customer">  
                <xsl:sort select="state"/>  
                <xsl:sort select="name"/>  
              </xsl:apply-templates>  
            </TABLE>  
          </BODY>  
        </HTML>  
      </xsl:template>  
      <xsl:template match="customer">  
        <TR>  
          <xsl:apply-templates select="name" />  
          <xsl:apply-templates select="address" />  
          <xsl:apply-templates select="phone" />  
        </TR>  
      </xsl:template>  
      <xsl:template match="name">  
        <TD STYLE="font-size:14pt font-family:serif">  
          <xsl:apply-templates />  
        </TD>  
      </xsl:template>  
      <xsl:template match="address">  
        <TD>  
          <xsl:apply-templates />  
        </TD>  
      </xsl:template>  
      <xsl:template match="phone">  
        <TD>  
          <xsl:apply-templates />  
        </TD>  
      </xsl:template>  
      <xsl:template match="phone" mode="accountNumber">  
        <xsl:param name="Area_Code"/>  
        <TD STYLE="font-style:italic">  
          1-<xsl:value-of select="."/>-001  
        </TD>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
2.  在 `<xsl:apply-templates select="phone" />` 之後插入資料指標並按 ENTER。 接著開始輸入下列 `xsl: apply-templates` 項目：  
  
    ```  
    <xsl:apply-templates select="phone"  mode="accountNumber">  
    ```  
  
     範本模式的清單會出現在 `mode=""` 項目的 `xsl:apply-templates` 屬性中。  
  
### <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>在 xsl:namespace-alias 項目的 stylesheet-prefix 和 result-prefix 屬性中使用 IntelliSense  
  
1.  建立新的 XSLT 檔案，並複製下列程式碼：  
  
    ```  
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"  
    version="1.0">  
      <xsl:param name="browser" select="'InternetExplorer'"/>  
      <xsl:template match="/">  
        <alt:stylesheet>  
          <xsl:choose>  
            <xsl:when test="$browser='InternetExplorer'">  
              <alt:import href="IERoutines.xsl"/>  
              <alt:template match="/">  
                <div>  
                  <alt:call-template name="showTable"/>  
                </div>  
              </alt:template>  
            </xsl:when>  
            <xsl:otherwise>  
              <alt:import href="OtherBrowserRoutines.xsl"/>  
              <alt:template match="/">  
                <div>  
                  <alt:call-template name="showTable"/>  
                </div>  
              </alt:template>  
            </xsl:otherwise>  
          </xsl:choose>  
        </alt:stylesheet>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
2.  在 `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` 之後插入資料指標並按 ENTER。 接著開始輸入下列 `xsl:namespace-alias` 項目：  
  
    ```  
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>  
    ```  
  
     請注意前置詞清單如何出現在 `stylesheet-prefix` 項目的 `result-prefix` 和 `xsl:namespace-alias` 屬性中。  
  
## <a name="see-also"></a>另請參閱  
 [XML 編輯器 IntelliSense 功能](../xml-tools/xml-editor-intellisense-features.md)



