---
title: VSCT XML 結構描述條件式屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 975ca2f5fa6f070baf07b26cbfa0d8c3aa3b67d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138352"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML 結構描述條件式屬性
條件式屬性可能會套用至所有清單和項目。 邏輯運算子和符號展開運算式評估為 true 或 false。 如果為 true，相關聯的清單或項目隨附於產生的輸出。  
  
 針對其他語彙基元的展開或常數，就可以測試權杖的擴充。 Defined() 函式用來測試是否已定義特定的名稱，即使它沒有任何值。  
  
 當條件屬性套用至清單時，條件被套用至清單中每個子元素。 如果子系項目本身包含條件屬性，然後其條件結合父運算式的 AND 運算。  
  
 評估為 true，值 1、 '1' 和 'true'，0、 '0' 和 'false' 評估為 false。  
  
## <a name="operators"></a>運算子  
 下列的運算子都可用來評估條件運算式。  
  
|運算子|定義|  
|--------------|----------------|  
|(,)|群組|  
|!|邏輯 NOT|  
|\<, >, \<=, >=, ==, !=|關係與相等|  
|和|Boolean|  
|或|Boolean|  
  
## <a name="examples"></a>範例  
  
```  
<Menu Condition="Defined(DEBUG)" ...  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" ...  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu ...  
        </Menu>  
    </Menus>  
  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)