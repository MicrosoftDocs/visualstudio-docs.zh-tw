---
title: 類別設計工具中的 Visual C++ 類別 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 04392545b5b5c352a35b9a3d523f0c6ff5d98b01
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54787072"
---
# <a name="visual-c-classes-in-class-designer"></a>類別設計工具中的 Visual C++ 類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

類別設計工具支援 C++ 類別，並以視覺化 Visual Basic 和 Visual C# 類別圖形的方式來視覺化原生 C++ 類別，差異在於 C++ 類別可以有多重繼承關聯性。 您可以展開類別圖形，以顯示類別中的更多欄位和方法，或將它摺疊以節省空間。  
  
> [!NOTE]
>  類別設計工具不支援等位 (配置的記憶體僅足以供等位的最大資料成員使用之類別的特殊類型)。  
  
## <a name="simple-inheritance"></a>簡單繼承  
 如果您將多個類別拖曳至類別圖表，而且類別具有類別繼承關聯性，則會使用箭號連接它們。 箭號會指向基底類別的方向。 例如，類別圖表中顯示下列類別時，會使用從 B 指向 A 的箭號連接它們：  
  
```  
class A {};  
class B : A {};  
```  
  
 您也可以只將類別 B 拖曳至類別圖表，並以滑鼠右鍵按一下 B 的類別圖形，然後按一下 [顯示基底類別]。 這會顯示其基底類別：A。  
  
## <a name="multiple-inheritance"></a>多重繼承  
 類別設計工具支援多重類別繼承關聯性的視覺效果。 衍生類別有多個基底類別的屬性時，會使用「多重繼承」。 以下是多重繼承的範例：  
  
```  
class Bird {};  
class Swimmer {};  
class Penguin : public Bird, public Swimmer {};  
```  
  
 如果您將多個類別拖曳至類別圖表，而且類別具有多重類別繼承關聯性，則會使用箭號連接它們。 箭號會指向基底類別的方向。  
  
 以滑鼠右鍵按一下類別圖形，然後按一下 [顯示基底類別] 會顯示所選取類別的基底類別。  
  
> [!NOTE]
>  [顯示衍生類別] 命令不支援用於 C++ 程式碼。 您可以移至 [類別檢視]、展開類型節點、展開 [衍生類型] 子資料夾，然後將這些類型拖曳至類別圖表，以顯示衍生類別。  
  
 如需多重類別繼承的詳細資訊，請參閱 [(NOTINBUILD) 多重繼承](http://msdn.microsoft.com/3b74185e-2beb-4e29-8684-441e51d2a2ca)和[多重基底類別](http://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740)。  
  
## <a name="abstract-classes"></a>抽象類別  
 類別設計工具支援抽象類別 (也稱為「抽象基底類別」)。 這些是您永遠不會具現化的類別，而是從中衍生其他類別的類別。 使用本文件稍早＜多重繼承＞中的範例，您可能會將 `Bird` 類別具現化為個別物件，如下所示︰  
  
```  
int main()  
{  
   Bird sparrow;  
   Bird crow;  
   Bird eagle;  
}  
```  
  
 不過，您可能不想要將 `Swimmer` 類別具現化為個別物件。 您可能只要從中衍生其他類型的動物類別；例如，`Penguin`、`Whale` 和 `Fish`。 在此情況下，您可以將 `Swimmer` 類別宣告為抽象基底類別。  
  
 若要將類別宣告為抽象，您可以使用 `abstract` 關鍵字。 標記為抽象或包括在抽象類別中的成員是虛擬的，而且必須由衍生自抽象類別的類別所實作。  
  
```  
class Swimmer abstract  
{  
   virtual void swim();  
   void dive();  
};  
```  
  
 您也可以包括至少一個純虛擬函式，以將類別宣告為抽象︰  
  
```  
class Swimmer  
{  
   virtual void swim() = 0;  
   void dive();  
};  
```  
  
 當您在類別圖表中顯示這些宣告時，類別名稱 `Swimmer` 和其純虛擬函式 `swim` 會以斜體顯示在抽象類別圖形中，以及標記法「抽象類別」。 請注意，抽象類別類型圖形與一般類別相同，差異在於其框線為點線。  
  
 衍生自抽象基底類別的類別必須覆寫基底類別中的每個純虛擬函式，否則無法具現化衍生類別。 因此，例如，如果 `Fish` 類別衍生自 `Swimmer` 類別，則 `Fish` 必須覆寫 `swim` 方法：  
  
```  
class Fish : public Swimmer  
{  
   void swim(int speed);  
};  
  
int main()  
{  
   Fish guppy;  
}  
```  
  
 當您在類別圖表中顯示此程式碼時，類別設計工具會繪製一條從 `Fish` 到 `Swimmer` 的繼承線。  
  
## <a name="anonymous-classes"></a>匿名類別  
 類別設計工具支援匿名類別。 「匿名類別類型」是未宣告識別碼的類別。 它們不能有建構函式或解構函式、不能當成引數傳遞至函式，而且不能從函式當成傳回值傳回。 您可以使用匿名類別，將類別名稱取代為 typedef 名稱，如下列範例所示︰  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
 結構也可以是匿名的。 類別設計工具顯示匿名類別和結構的方式，與顯示對應類型相同。 雖然您可以宣告和顯示匿名類別和結構，但是類別設計工具不會使用您指定的標記名稱。 它會使用類別檢視所產生的名稱。 在類別檢視和類別設計工具中，類別或結構會顯示為稱為 **__unnamed** 的項目。  
  
 如需匿名類別的詳細資訊，請參閱[匿名類別類型](http://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8)。  
  
## <a name="template-classes"></a>範本類別  
 類別設計工具支援範本類別的視覺效果。 支援巢狀宣告。 下表顯示一些典型宣告。  
  
|程式碼項目|類別設計工具檢視|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> 範本類別|  
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> 範本類別|  
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> 範本類別|  
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> 範本類別|  
  
 下表顯示一些部分特製化範例。  
  
|程式碼項目|類別設計工具檢視|  
|------------------|-------------------------|  
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> 範本類別|  
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> 範本類別|  
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> 範本類別|  
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> 範本類別|  
  
 下表顯示部分特製化中的一些繼承範例。  
  
|程式碼項目|類別設計工具檢視|  
|------------------|-------------------------|  
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> 範本類別<br /><br /> `B`<br /><br /> 類別<br /><br /> (指向類別 A)<br /><br /> `C`<br /><br /> 類別<br /><br /> (指向類別 A)|  
  
 下表顯示一些部分特製化範本函式範例。  
  
|程式碼項目|類別設計工具檢視|  
|------------------|-------------------------|  
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func\<T, U> (+ 1 個多載)|  
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> 範本類別<br /><br /> `B<T2>`<br /><br /> 範本類別<br /><br /> (B 包含在「巢狀類型」的類別 A 內)|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> 類別<br /><br /> -> C\<int><br /><br /> `C<T>`<br /><br /> 範本類別|  
  
 下表顯示一些範本繼承範例。  
  
|程式碼項目|類別設計工具檢視|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> 類別<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> 類別<br /><br /> (B 包含在「巢狀類型」的類別 C 內)<br /><br /> `C<T>`<br /><br /> 範本類別|  
  
 下表顯示一些標準特製化類別連接範例。  
  
|程式碼項目|類別設計工具檢視|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> 類別<br /><br /> ->C\<int><br /><br /> `C<int>`<br /><br /> 類別<br /><br /> `C<T>`<br /><br /> 範本類別<br /><br /> `D`<br /><br /> 類別<br /><br /> ->C\<float>|  
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T>|  
  
## <a name="see-also"></a>請參閱  
 [使用 Visual C++ 程式碼 (類別設計工具)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [類別和結構](http://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [匿名類別類型](http://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8)   
 [(NOTINBUILD) 多重繼承](http://msdn.microsoft.com/3b74185e-2beb-4e29-8684-441e51d2a2ca)   
 [多重基底類別](http://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740)   
 [範本](http://msdn.microsoft.com/library/90fcc14a-2092-47af-9d2e-dba26d25b872)
