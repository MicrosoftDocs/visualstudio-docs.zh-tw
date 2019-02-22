---
title: Microsoft Fakes 中的程式碼產生、編譯和命名慣例 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 20221de4-2a9e-4787-b99a-b5855bb90872
caps.latest.revision: 18
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 70392f50ecd13539012672bf71900c30845af734
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54783367"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Microsoft Fakes 中的程式碼產生、編譯和命名慣例
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題討論產生與編譯 Fakes 程式碼的選項和問題，並且描述 Fakes 產生類型、成員和參數的命名慣例。  
  
 **需求**  
  
-   Visual Studio 企業版  
  
##  <a name="BKMK_In_this_topic"></a>本主題內容  
 [程式碼產生和編譯](#BKMK_Code_generation_and_compilation)  
  
- [設定 Stub 的程式碼產生](#BKMK_Configuring_code_generation_of_stubs) • [類型篩選](#BKMK_Type_filtering) • [設定具象類別及虛擬方法的 Stub](#BKMK_Stubbing_concrete_classes_and_virtual_methods) • [內部類型](#BKMK_Internal_types) • [最佳化建置時間](#BKMK_Optimizing_build_times) • [避免組件名稱發生衝突](#BKMK_Avoiding_assembly_name_clashing)  
  
  [Fakes 命名慣例](#BKMK_Fakes_naming_conventions)  
  
- [填充碼類型和 Stub 類型命名慣例](#BKMK_Shim_type_and_stub_type_naming_conventions) • [填充碼委派屬性或 Stub 委派欄位命名慣例](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions) • [參數類型命名慣例](#BKMK_Parameter_type_naming_conventions) • [遞迴規則](#BKMK_Recursive_rules)  
  
  [外部資源](#BKMK_External_resources)  
  
- [指引](#BKMK_Guidance)  
  
##  <a name="BKMK_Code_generation_and_compilation"></a> 程式碼產生和編譯  
  
###  <a name="BKMK_Configuring_code_generation_of_stubs"></a> 設定 Stub 的程式碼產生  
 虛設常式類型會在有 .fakes 副檔名的 XML 檔中設定產生 。 Fakes 框架會在建置流程中透過自訂 MSBuild 工作整合，並在建置期間偵測這些檔案。 Fakes 程式碼產生器會編譯虛設常式類型至組件內，並加入專案參考。  
  
 下列範例說明在 FileSystem.dll 中定義的虛設常式類型：  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
    <Assembly Name="FileSystem"/>  
</Fakes>  
  
```  
  
###  <a name="BKMK_Type_filtering"></a> 類型篩選  
 篩選條件可以在 .fakes 檔案中設定，以限制應該設定哪些虛設常式類型。 您可以在 StubGeneration 項目下加入 Clear、Add、Remove 項目的未繫結數目，已建置所選類型的清單。  
  
 例如，這個 .fakes 檔案會針對在 System 和 System.IO 命名空間下的類型產生虛設常式，但是排除 System 中任何包含 "Handle" 的類型：  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
  <Assembly Name="mscorlib" />  
  <!-- user code -->  
  <StubGeneration>  
    <Clear />  
    <Add Namespace="System!" />  
    <Add Namespace="System.IO!"/>  
    <Remove TypeName="Handle" />  
  </StubGeneration>  
  <!-- /user code -->  
</Fakes>  
```  
  
 篩選字串會使用簡單文法定義應該如何完成比對：  
  
-   篩選條件預設不區分大小寫；篩選條件會執行子字串比對：  
  
     `el` 比對 "hello"  
  
-   將 `!` 加入篩選條件結尾會讓它變成精確區分大小寫的比對：  
  
     `el!` 不符合 "hello"  
  
     `hello!` 比對 "hello"  
  
-   將 `*` 加入篩選條件的結尾會讓它符合字串的前置詞：  
  
     `el*` 不符合 "hello"  
  
     `he*` 比對符合 "hello"  
  
-   以分號分隔之清單中的多個篩選條件會結合為分離：  
  
     `el;wo` 比對符合 "hello" 和 "world"  
  
###  <a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a> 設定具象類別及虛擬方法的 Stub  
 預設會為所有非密封類別產生虛設常式類型。 透過 .fakes 組態檔可將虛設常式類型限制為抽象類別：  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
  <Assembly Name="mscorlib" />  
  <!-- user code -->  
  <StubGeneration>  
    <Types>  
      <Clear />  
      <Add AbstractClasses="true"/>  
    </Types>  
  </StubGeneration>  
  <!-- /user code -->  
</Fakes>  
```  
  
###  <a name="BKMK_Internal_types"></a> 內部類型  
 Fakes 程式碼產生器會針對所產生之 Fakes 組件的可見類型產生填充碼和虛設常式類型。 若要讓 Fakes 和測試組件看見填充組件的內部類型，請將 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性加入填充組件的程式碼，以提供可視性給所產生的 Fakes 組件和測試組件。 以下為範例：  
  
```csharp  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes")]  
[assembly: InternalsVisibleTo("FileSystem.Tests")]  
```  
  
 **強式名稱組件中的內部類型**  
  
 如果填充組件為強式名稱，而且您想要存取組件的內部類型：  
  
- 您的測試組件和 Fakes 組件都必須具有強式名稱。  
  
- 您必須將測試的公開金鑰和 Fakes 組件加入至填充組件的 **InternalsVisibleToAttribute** 屬性。 以下說明在填充組件程式碼以強式名稱命名時，填充組件程式碼中的範例屬性樣貌：  
  
  ```csharp  
  // FileSystem\AssemblyInfo.cs  
  [assembly: InternalsVisibleTo("FileSystem.Fakes",  
      PublicKey=<Fakes_assembly_public_key>)]  
  [assembly: InternalsVisibleTo("FileSystem.Tests",  
      PublicKey=<Test_assembly_public_key>)]  
  ```  
  
  如果填充組件具有強式名稱，則 Fakes 架構會自動強式簽署產生的 Fakes 組件。 您必須強式簽署測試組件。 請參閱[建立和使用強式名稱的組件](http://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9)。  
  
  Fakes 架構會使用相同金鑰來簽署所有產生的組件，因此，您可以使用這個程式碼片段做為起點，來將 Fakes 組件的 **InternalsVisibleTo** 屬性加入至填充組件程式碼。  
  
```csharp  
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]  
```  
  
 您可以針對 Fakes 組件指定不同的公用金鑰，例如您已針對填充組件建立的金鑰，方法是指定 **.snk** 檔案的完整路徑，其中包含替代金鑰做為 **.fakes** 檔案之 `Fakes`\\`Compilation` 項目中的 `KeyFile` 屬性值。 例如：  
  
```xml  
<-- FileSystem.Fakes.fakes -->  
<Fakes ...>  
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />  
</Fakes>  
  
```  
  
 接著您必須在填充組件程式碼中，使用替代 **.snk** 檔案的公開金鑰，做為 Fakes 組件中 InternalVisibleTo 屬性的第二個參數：  
  
```csharp  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes",  
    PublicKey=<Alternate_public_key>)]  
[assembly: InternalsVisibleTo("FileSystem.Tests",  
    PublicKey=<Test_assembly_public_key>)]  
```  
  
 在上面的範例中，`Alternate_public_key` 和 `Test_assembly_public_key` 兩個值可以是相同的。  
  
###  <a name="BKMK_Optimizing_build_times"></a> 最佳化建置時間  
 編譯 Fakes 組件可能大幅增加建置時間。 您也可以藉由在不同的集中式專案中產生 .NET System 組件的 Fake 組件和協力廠商組件，以最小化建置時間。 因為這類組件在電腦上極少變動，您可以在其他專案中重複使用產生的 Fakes 組件。  
  
 從單元測試專案中，您可以取得已編譯 Fakes 組件的參考，這些組件是放置在專案資料夾中的 FakesAssemblies 底下。  
  
1.  建立 .NET 執行階段版本與測試專案相符的新類別庫， 並稱它為 Fakes.Prebuild。 從專案刪除不需要的 class1.cs 檔。  
  
2.  將參考加入您所需之 Fakes 的所有系統和協力廠商組件。  
  
3.  為每個組件和組建加入 .fakes 檔案。  
  
4.  從您的測試專案  
  
    -   確定您有 Fakes 執行階段 DLL 的參考：  
  
         C:\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll  
  
    -   對於您已建立 Fakes 的每個組件，加入專案之 Fakes.Prebuild\FakesAssemblies 資料夾中對應 DLL 檔案的參考。  
  
###  <a name="BKMK_Avoiding_assembly_name_clashing"></a> 避免組件名稱發生衝突  
 在 Team Build 環境中，所有組建輸出會合併到單一目錄。 在多個專案使用 Fakes 的情況下，可能會發生不同版本的 Fakes 組件彼此覆寫的情形。 例如，.NET Framework 2.0 的 TestProject1 fakes mscorlib.dll 與 .NET Framework 4 的 TestProject2 fakes mscorlib.dll 都會產生 mscorlib.Fakes.dll Fakes 組件。  
  
 若要避免這個問題，當加入 .fakes 檔時，Fake 應該會自動為非專案參考建立版本限定的 Fake 組件名稱。 當您建立 Fakes 組件名稱時，版本限定的 Fakes 組件名稱會嵌入版本號碼：  
  
 假設組件 MyAssembly 和版本 1.2.3.4，則 Fakes 組件名稱為 MyAssembly.1.2.3.4.Fakes。  
  
 您可以透過編輯 .fakes 中 Assembly 項目的 Version 屬性來變更或移除這個版本：  
  
```xml  
attribute of the Assembly element in the .fakes:  
<Fakes ...>  
  <Assembly Name="MyAssembly" Version="1.2.3.4" />  
  ...  
</Fakes>  
  
```  
  
##  <a name="BKMK_Fakes_naming_conventions"></a> Fakes 命名慣例  
  
###  <a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a> 填充碼類型和 Stub 類型命名慣例  
 **命名空間**  
  
- .Fakes 後置字元會加入命名空間。  
  
   例如， `System.Fakes` 命名空間包含系統命名空間的填充碼類型。  
  
- Global.Fakes 包含空白命名空間的填充碼類型。  
  
  **類型名稱**  
  
- 填充碼前置詞會加入類型名稱，以建置填充碼類型名稱。  
  
   例如，ShimExample 是範例類型的填充碼類型。  
  
- 虛設常式前置詞會加入類型名稱，以建置虛設常式類型名稱。  
  
   例如，StubIExample 是 IExample 類型的虛設常式類型。  
  
  **類型引數和巢狀類型結構**  
  
- 會複製泛型型別引數。  
  
- 會針對填充碼類型複製巢狀類型結構。  
  
###  <a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a> 填充碼委派屬性或 stub 委派欄位命名慣例  
 欄位命名適用的**基本規則**，從空白名稱開始：  
  
- 會附加方法名稱。  
  
- 如果方法名稱是明確的介面實作，則會將點移除。  
  
- 如果方法為泛型，則會附加 `Of`*n*，其中 *n* 是泛型方法引數的數目。  
  
  **特殊方法名稱**，例如屬性 getter 或 setter，會依照下表所述加以處理。  
  
|如果方法是...|範例|附加的方法名稱|  
|-------------------|-------------|--------------------------|  
|**建構函式**|`.ctor`|`Constructor`|  
|靜態**建構函式**|`.cctor`|`StaticConstructor`|  
|方法名稱由兩個以 "_" 分隔的部分 (例如屬性 getter) 組成的**存取子**|*kind_name* (一般情況，但 ECMA 不會強制執行)|*NameKind*，其中這兩個部分會改成大寫並互換|  
||`Prop` 屬性的 getter|`PropGet`|  
||`Prop` 屬性的 setter|`PropSet`|  
||事件 adder|`Add`|  
||事件 remover|`Remove`|  
|由兩個部分組成的**運算子**|`op_name`|`NameOp`|  
|例如：+ 運算子|`op_Add`|`AddOp`|  
|若是**轉換運算子**，會附加傳回類型。|`T op_Implicit`|`ImplicitOpT`|  
  
 **備註**  
  
-   **索引子的 getter 和 setter** 是以類似屬性的方式來處理。 索引子的預設名稱是 `Item`。  
  
-   會轉換並串連**參數類型**名稱。  
  
-   除非有多載模稜兩可的情況，否則會忽略**傳回類型**。 如果是這種情況，則傳回型別將會附加在名稱結尾。  
  
###  <a name="BKMK_Parameter_type_naming_conventions"></a> 參數類型命名慣例  
  
|假設|附加的字串是...|  
|-----------|-------------------------|  
|**類型**`T`|T<br /><br /> 命名空間、巢狀結構和泛型 tics 會被丟棄。|  
|**out 參數**`out T`|`TOut`|  
|**ref 參數** `ref T`|`TRef`|  
|**陣列類型**`T[]`|`TArray`|  
|**多維陣列**類型 `T[ , , ]`|`T3`|  
|**指標**類型 `T*`|`TPtr`|  
|**泛型類型**`T<R1, …>`|`TOfR1`|  
|類型 `C<TType>` 的**泛型類型引數**`!i`|`Ti`|  
|方法 `M<MMethod>` 的**泛型方法引數**`!!i`|`Mi`|  
|**巢狀類型**`N.T`|會附加 `N`，後接 `T`|  
  
###  <a name="BKMK_Recursive_rules"></a> 遞迴規則  
 下列規則會遞迴套用：  
  
-   由於 Fakes 會使用 C# 來產生 Fakes 組件，因此任何會產生無效 C# 語彙基元的字元都會逸出為 "_" (底線)。  
  
-   如果產生的名稱與宣告類型的任何成員發生衝突，則會使用編號配置，方法是附加兩位數計數器，從 01 開始。  
  
##  <a name="BKMK_External_resources"></a> 外部資源  
  
###  <a name="BKMK_Guidance"></a> 指引  
 [使用 Visual Studio 2012 測試持續傳遞 - 第 2 章：單元測試：測試內部](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>請參閱  
 [使用 Microsoft Fakes 在測試期間隔離程式碼](../test/isolating-code-under-test-with-microsoft-fakes.md)
