---
title: 重構程式碼
description: 使用來源分析，可讓在 Visual Studio for Mac 中重新組織程式碼更為簡單。
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.openlocfilehash: ec0ae7aa61275b9b5362db178b9bdb8e3ccedfbb
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33884192"
---
# <a name="refactoring"></a>重構

重構程式碼是重新排列、重建和釐清現有程式碼的方法，並能同時確保程式碼的整體行為不會變更。

重構會產生較健康的程式碼基底，以讓您、任何其他開發人員或可能參考程式碼的使用者更容易使用、讀取和維護它。

Visual Studio for Mac 與 Roslyn (Microsoft 的開放原始碼 .NET 編譯器平台) 的整合，可讓您進行更多重構作業。

## <a name="renaming"></a>重新命名 

[重新命名] 重構命令可以用於任何程式碼識別碼 (例如，類別名稱、屬性名稱等等)，以尋找該識別碼的所有出現項目並進行變更。 若要重新命名符號，請以滑鼠右鍵按一下它，然後選擇 [重構] > [重新命名]，或 **Cmd + R** 按鍵繫結關係：

![重新命名功能表項目](media/refactoring-renaming1.png)

這會反白顯示符號和其任何參考。 當您開始鍵入新名稱時，會自動變更您程式碼中的所有參考，並且按 **Enter** 以發出重新命名完成的訊號：

 ![重新命名和識別碼](media/refactoring-renaming2.png)

## <a name="context-actions"></a>內容動作

內容動作可讓您檢查任何 C# 程式碼，並查看所有可能的重構選項。 

[解析] 和 [重構] 內容項目會合併至可提供所有可用內容動作的單一 [快速檢修] 項目：

![顯示內容項目](media/refactoring-context-action.png)

將滑鼠游標移至任何內容動作上方，可提供從程式碼中新增或移除之項目的預覽。

或者，您可以在程式碼中的任何位置按 **Option + Enter**：

![選項輸入內容項目](media/refactoring-image2a.png)

若要啟用這些選項，您必須選取 [Visual Studio for Mac] > [喜好設定] > [文字編輯器] > [來源分析] 選項中的 [啟用開啟檔案的來源分析]：

 ![啟用來源分析](media/refactoring-options.png)

可建議超過 100 個可能的動作，其啟用或停用方式是瀏覽至 [Visual Studio for Mac] > [喜好設定] > [來源分析] > [C#] > [程式碼動作]，並選取或取消選取動作旁的方塊：

 ![C# 來源分析動作](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>一般內容動作

下面將說明一些最常用內容動作。

#### <a name="extract-method"></a>擷取方法

擷取方法重構作業可讓您擷取現有成員中的程式碼選取項目來建立新的方法。 此動作將會執行兩個作業：

* 建立包含所選取程式碼的新方法
* 在所選取程式碼所在的位置中，呼叫新方法。

##### <a name="example"></a>範例

1. 加入下列程式碼：

```
    class MainClass
    {

        double CalculatePyramidVolume(double baseArea, double height)
        {

            double volume = (baseArea * height) / 3;

            return volume;
        }
    }
```

2. 反白顯示 `double volume = (baseArea * height) / 3;` 這行，並以滑鼠右鍵按一下它，然後選取 [重構] > [擷取方法]。

3. 使用方向鍵來選取新方法在程式碼中的位置。


#### <a name="encapsulate-field"></a>封裝欄位

[封裝欄位] 作業可讓您從現有欄位建立屬性，並更新您的程式碼以參考新建立的屬性。 建立可封裝您欄位的屬性，即會禁止直接存取您的公用欄位，這表示其他物件無法修改它。

此動作將會執行下列作業：

* 將存取修飾詞變更為私用。
* 產生欄位的 getter 和 setter (除非欄位為唯讀，在此情況下，它只會建立 getter)。


## <a name="source-analysis"></a>來源分析

來源分析透過將潛在錯誤和樣式違規加上底線，並將自動修正提供為內容動作，來即時分析您的程式碼。 

檢視文字編輯器右側的捲軸，即可隨時檢視任何檔案的所有來源分析結果：

 ![來源分析提要欄位](media/refactoring-image4a.png)

如果您按一下頂端的圓圈，則可以逐一查看每項建議，而最高嚴重性問題會顯示在最前面。 將滑鼠游標移至個別結果或個別行上方，將會顯示問題，這可透過內容動作進行修正：

 ![來源分析項目](media/refactoring-image5.png)

