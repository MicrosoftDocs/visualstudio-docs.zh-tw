---
title: .VSCT XML 架構條件式屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6294ee8027b61840149096561efc91b8a4a3c3ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422145"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML 結構描述條件式屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

條件屬性可套用至所有清單和專案。 邏輯運算子和符號展開運算式的評估結果為 true 或 false。 若為 true，則產生的輸出中會包含相關聯的清單或專案。  
  
 您可以針對其他標記展開或常數測試標記擴充。  ( # A1 定義的函式會用來測試是否已定義特定名稱，即使沒有值也是一樣。  
  
 當 Condition 屬性套用至清單時，此條件會套用至清單中的每個子項目。 如果子項目本身包含 Condition 屬性，則它的條件會與 AND 運算的父運算式結合。  
  
 值1、' 1 ' 和 ' true ' 會評估為 true，而0、' 0 ' 和 ' false ' 會評估為 false。  
  
## <a name="operators"></a>操作員  
 您可以使用下列運算子來評估條件運算式。  
  
|運算子|定義|  
|--------------|----------------|  
|(,)|群組|  
|!|邏輯 NOT|  
|\<, >, \<=, >=, ==, !=|關係與相等|  
|及|Boolean|  
|或|Boolean|  
  
## <a name="examples"></a>範例  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
