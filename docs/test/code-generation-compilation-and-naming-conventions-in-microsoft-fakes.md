---
title: Microsoft Fakes：產生 & 編譯器代碼;命名慣例
description: 瞭解 Fakes 程式碼產生和編譯的選項和問題，包括 Fakes 所產生類型、成員和參數的命名慣例。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ecba59e633bf6d456f16e6098f47719e052ac0de
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2021
ms.locfileid: "100006358"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Microsoft Fakes 中的程式碼產生、編譯和命名慣例

本文討論產生與編譯 Fakes 程式碼的選項和問題，並且描述 Fakes 產生類型、成員和參數的命名慣例。

**需求**

- Visual Studio Enterprise
- .NET Framework 專案
::: moniker range=">=vs-2019"
- 在 Visual Studio 2019 Update 6 中預覽的 .NET Core、.NET 5.0 和 SDK 樣式專案支援，預設會在 Update 8 中啟用。 如需詳細資訊，請參閱 [適用于 .Net Core 和 SDK 樣式專案的 Microsoft Fakes](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects)。
::: moniker-end

## <a name="code-generation-and-compilation"></a>程式碼產生和編譯

### <a name="configure-code-generation-of-stubs"></a>設定虛設常式的程式碼產生

虛設常式類型會在有 *.fakes* 副檔名的 XML 檔中設定產生。 Fakes 框架會在建置流程中透過自訂 MSBuild 工作整合，並在建置期間偵測這些檔案。 Fakes 程式碼產生器會編譯虛設常式類型至組件內，並加入專案參考。

下列範例說明在 *FileSystem.dll* 中定義的虛設常式類型：

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>類型篩選

篩選條件可以在 *.fakes* 檔案中設定，以限制應該設定哪些虛設常式類型。 您可以在 StubGeneration 項目下加入 Clear、Add、Remove 項目的未繫結數目，已建置所選類型的清單。

例如，下列 *fakes* 檔案會針對 system 和 System.IO 命名空間下的類型產生存根，但是在系統中排除任何包含 "Handle" 的類型：

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

- 篩選條件預設不區分大小寫；篩選條件會執行子字串比對：

     `el` 比對符合 "hello"

- 將 `!` 新增至篩選條件結尾會讓它變成精確區分大小寫的比對：

     `el!` 不符合 "hello"

     `hello!` 比對符合 "hello"

- 將 `*` 新增至篩選條件的結尾會讓它符合字串的前置詞：

     `el*` 不符合 "hello"

     `he*` 比對符合 "hello"

- 以分號分隔之清單中的多個篩選條件會結合為分離：

     `el;wo` 比對符合 "hello" 和 "world"

### <a name="stub-concrete-classes-and-virtual-methods"></a>設定具象類別及虛擬方法的虛設常式

預設會為所有非密封類別產生虛設常式類型。 透過 *.fakes* 組態檔可將虛設常式類型限制為抽象類別：

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

### <a name="internal-types"></a>內部類型

Fakes 程式碼產生器會針對所產生之 Fakes 組件的可見類型產生填充碼和虛設常式類型。 若要讓 Fakes 和測試組件看見填充組件的內部類型，請將 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性加入填充組件的程式碼，以提供可視性給所產生的 Fakes 組件和測試組件。 以下為範例：

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

**強式名稱組件中的內部類型**

如果填充組件為強式名稱，而且您想要存取組件的內部類型：

- 您的測試組件和 Fakes 組件都必須具有強式名稱。

- 請將測試的公開金鑰和 Fakes 組件新增至填充組件的 **InternalsVisibleToAttribute** 屬性。 以下說明在填充組件以強式名稱命名時，填充組件程式碼中的範例屬性樣貌：

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

如果填充組件具有強式名稱，則 Fakes 架構會自動強式簽署產生的 Fakes 組件。 您必須強式簽署測試組件。 請參閱 [強式名稱的元件](/dotnet/framework/app-domains/strong-named-assemblies)。

Fakes 架構會使用相同金鑰來簽署所有產生的組件，因此，您可以使用這個程式碼片段做為起點，來將 Fakes 組件的 **InternalsVisibleTo** 屬性加入至填充組件程式碼。

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

您可以指定 Fakes 元件的不同公開金鑰，例如您針對填充元件建立的索引鍵，方法是指定 *.snk* 檔案的完整路徑，該檔案中包含的替代索引鍵做為 `KeyFile` `Fakes` \\ `Compilation` *Fakes* 檔案之元素中的屬性值。 例如：

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

接著您必須在填充組件程式碼中，使用替代 *.snk* 檔案的公開金鑰，做為 Fakes 組件中 InternalVisibleTo 屬性的第二個參數：

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

在上面的範例中，`Alternate_public_key` 和 `Test_assembly_public_key` 兩個值可以是相同的。

### <a name="optimize-build-times"></a>最佳化建置時間

編譯 Fakes 組件可能大幅增加建置時間。 您也可以藉由在不同的集中式專案中產生 .NET System 組件的 Fake 組件和協力廠商組件，以最小化建置時間。 因為這類組件在電腦上極少變動，您可以在其他專案中重複使用產生的 Fakes 組件。

從單元測試專案中，請新增已編譯 Fakes 組件的參考，這些組件是放置在專案資料夾中的 FakesAssemblies 底下。

1. 建立 .NET 執行階段版本與測試專案相符的新類別庫， 並稱它為 Fakes.Prebuild。 從專案移除 *class1.cs* 檔案，而不需要。

2. 將參考加入您所需之 Fakes 的所有系統和協力廠商組件。

3. 為每個組件和組建新增 *.fakes* 檔案。

4. 從您的測試專案

    - 確定您有 Fakes 執行階段 DLL 的參考：

         *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    - 對於您已建立 Fakes 的每個組件，新增專案之 *Fakes.Prebuild\FakesAssemblies* 資料夾中對應 DLL 檔案的參考。

### <a name="avoid-assembly-name-clashing"></a>避免組件名稱發生衝突

在 Team Build 環境中，所有組建輸出會合併到單一目錄。 如果多個專案使用 Fakes，可能會發生不同版本的 Fakes 組件彼此覆寫的情形。 例如，.NET Framework 2.0 的 TestProject1 fakes *mscorlib.dll* 與 .NET Framework 4 的 TestProject2 fakes *mscorlib.dll* 都會產生 *mscorlib.Fakes.dll* Fakes 組件。

若要避免這個問題，當新增 *.fakes* 檔時，Fakes 應該會自動為非專案參考建立版本限定的 Fakes 組件名稱。 當您建立 Fakes 組件名稱時，版本限定的 Fakes 組件名稱會嵌入版本號碼：

假設組件 MyAssembly 和版本 1.2.3.4，則 Fakes 組件名稱為 MyAssembly.1.2.3.4.Fakes。

您可以透過編輯 *.fakes* 中 Assembly 項目的 Version 屬性來變更或移除這個版本：

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>
```

## <a name="fakes-naming-conventions"></a>Fakes 命名慣例

### <a name="shim-type-and-stub-type-naming-conventions"></a>填充碼類型和虛設常式類型命名慣例

**命名空間**

- .Fakes 後置字元會加入命名空間。

   例如， `System.Fakes` 命名空間包含系統命名空間的填充碼類型。

- Global.Fakes 包含空白命名空間的填充碼類型。

  **型別名稱**

- 填充碼前置詞會加入類型名稱，以建置填充碼類型名稱。

   例如，ShimExample 是範例類型的填充碼類型。

- 虛設常式前置詞會加入類型名稱，以建置虛設常式類型名稱。

   例如，StubIExample 是 IExample 類型的虛設常式類型。

  **類型引數和巢狀類型結構**

- 會複製泛型型別引數。

- 會針對填充碼類型複製巢狀類型結構。

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>填充碼委派屬性或虛設常式委派欄位命名慣例

欄位命名適用的 **基本規則**，從空白名稱開始：

- 會附加方法名稱。

- 如果方法名稱是明確的介面實作，則會將點移除。

- 如果方法為泛型，則會附加 `Of`*n*，其中 *n* 是泛型方法引數的數目。

  **特殊方法名稱**，例如屬性 getter 或 setter，會依照下表所述加以處理：

|如果方法是...|範例|附加的方法名稱|
|-|-|-|
|**函數**|`.ctor`|`Constructor`|
|靜態 **建構函式**|`.cctor`|`StaticConstructor`|
|方法名稱由兩個以 "_" 分隔的部分 (例如屬性 getter) 組成的 **存取子**|*kind_name* (一般情況，但 ECMA 不會強制執行)|*NameKind*，其中這兩個部分會改成大寫並互換|
||`Prop` 屬性的 getter|`PropGet`|
||`Prop` 屬性的 setter|`PropSet`|
||事件 adder|`Add`|
||事件 remover|`Remove`|
|由兩個部分組成的 **運算子**|`op_name`|`NameOp`|
|例如：+ 運算子|`op_Add`|`AddOp`|
|若是 **轉換運算子**，會附加傳回類型。|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **索引子的 getter 和 setter** 是以類似屬性的方式來處理。 索引子的預設名稱是 `Item`。
> - 會轉換並串連 **參數類型** 名稱。
> - 除非有多載不明確，否則會忽略傳回 **型** 別。 如果有多載模稜兩可的情況，則傳回型別將會附加在名稱結尾。

### <a name="parameter-type-naming-conventions"></a>參數類型命名慣例

|假設|附加的字串是...|
|-|-|
|**類型**`T`|T<br /><br /> 命名空間、巢狀結構和泛型 tics 會被丟棄。|
|**Out 參數**`out T`|`TOut`|
|**ref 參數** `ref T`|`TRef`|
|**陣列類型**`T[]`|`TArray`|
|**多維陣列** 類型 `T[ , , ]`|`T3`|
|**指標** 類型 `T*`|`TPtr`|
|**泛型型** 別`T<R1, ...>`|`TOfR1`|
|型 **別的泛型型別引數** `!i``C<TType>`|`Ti`|
|方法的 **泛型方法引數** `!!i``M<MMethod>`|`Mi`|
|**巢狀型別**`N.T`|會附加 `N`，後接 `T`|

### <a name="recursive-rules"></a>遞迴規則

下列規則會遞迴套用：

- 由於 Fakes 會使用 C# 來產生 Fakes 組件，因此任何會產生無效 C# 語彙基元的字元都會逸出為 "_" (底線)。

- 如果產生的名稱與宣告類型的任何成員發生衝突，則會使用編號配置，方法是附加兩位數計數器，從 01 開始。

## <a name="see-also"></a>另請參閱

- [使用 Microsoft Fakes 隔離測試中的程式碼](../test/isolating-code-under-test-with-microsoft-fakes.md)
