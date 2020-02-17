---
title: 使用C++核心指導方針檢查 |Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 946b46bfb5101154832e10b61cd861b0c104dc14
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275295"
---
# <a name="using-the-c-core-guidelines-checkers"></a>使用 C++ Core Guidelines 檢查工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++核心指導方針是一組可攜的指導方針、規則，以及有關專家和C++設計人員C++所建立之程式碼的最佳作法。  Visual Studio 現在支援增益集封裝，可為程式碼分析工具建立額外的規則，以檢查您的程式碼C++是否符合核心指導方針和建議改進。  
  
## <a name="the-c-core-guidelines-project"></a>C++核心指導方針專案  
 C++核心指導方針是由 Bjarne Stroustrup 和其他人所建立，是安全且C++有效率地使用新式的指南。 這些指導方針強調靜態型別安全和資源安全性。 它們會找出用來消除或減少語言中最容易出錯之部分的方法，並建議如何讓您的程式碼更簡單，並以可靠的方式提供更佳的效能。 這些指導方針是由標準C++基礎所維護。 若要深入瞭解，請參閱[GitHub](https://github.com/isocpp/CppCoreGuidelines)上的檔集、 [ C++核心指導方針](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)和存取C++核心指導方針檔專案檔。  
  
 Microsoft 藉由C++製作C++可使用 Nuget 套件新增至專案的核心檢查程式碼分析規則集，來支援核心方針的工作。 此套件的名稱為 CppCoreCheck，並可在[https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck)取得。 此套件要求您至少安裝了 Visual Studio 2015 Update 1。  
  
 此套件也會安裝另一個套件做為相依性，也就是僅限標頭的指導方針支援程式庫（GSL）。 GitHub 上的[https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)也提供 GSL。  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>啟用程式C++代碼分析中的核心檢查方針  
 若要啟用C++核心檢查程式碼分析工具，請將 CppCoreCheck NuGet 套件安裝到您C++要在 Visual Studio 內檢查的每個專案。  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>若要將 CppCoreCheck 套件新增至您的專案  
  
1. 在**方案總管**中，以滑鼠右鍵按一下您要新增封裝之方案中的專案內容功能表。 選擇 [**管理 Nuget 套件**] 以開啟 [ **nuget 套件管理員**]。  
  
2. 在 [ **NuGet 套件管理員**] 視窗中，搜尋 CppCoreCheck。  
  
    ![[Nuget 套件管理員] 視窗會顯示 CppCoreCheck 套件](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. 選取 [CppCoreCheck] 套件，然後選擇 [**安裝**] 按鈕，將規則新增至您的專案。  
  
   NuGet 套件會將額外的 MSBuild .targets 檔案新增至您的專案，當您在專案上啟用程式碼分析時，就會叫用這個檔案。 這個 .targets 檔案會將C++核心檢查規則新增為 Visual Studio 程式碼分析工具的額外延伸模組。  
  
   您可以在專案的 [**屬性頁**] 對話方塊的 [程式**代碼分析**] 區段中，選取 [**在組建上啟用程式碼分析**] 核取方塊，以啟用專案的程式碼分析。  
  
   ![程式碼分析一般設定的屬性頁](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   C++核心檢查規則會成為在啟用程式碼分析時所執行之預設規則集的一部分。 由於C++核心檢查規則正在開發中，因此某些規則可能不會準備好用於所有程式碼，但在開發期間可能會有資訊。 這些規則會以實驗性的形式發行。 您可以選擇是否要在專案的屬性中執行已發行或實驗性規則。  
  
   ![程式碼分析延伸模組設定的屬性頁](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   若要啟用或停C++用核心檢查規則集，請開啟專案的 [**屬性頁**] 對話方塊。 在 [設定**屬性**] 底下，展開 [程式**代碼分析**，**延伸**模組]。 在 [**啟用C++核心檢查（已發行）** ] 或 [**啟用C++核心檢查（實驗性）** ] 旁的下拉式控制項中，選擇 [**是]** 或 [**否**]。 選擇 **[確定]** **或 [** 套用] 以儲存變更。  
  
## <a name="check-types-bounds-and-lifetimes"></a>檢查類型、界限和存留期  
 C++核心檢查套件目前包含[型別安全](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type)、[界限安全](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)和[存留期安全](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime)設定檔的檢查。  
  
 以下是C++核心檢查規則可以找到的問題種類範例：  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 這個範例會示範C++核心檢查規則可以找到的幾個警告：  
  
- C26494 是規則類型。5：一律初始化物件。  
  
- C26485 是規則界限。3：沒有陣列到指標的衰減。  
  
- C26481 是規則界限。1：不要使用指標算術。 請改用 `span`。  
  
  當您C++編譯此程式碼時，如果已安裝並啟用核心檢查程式碼分析規則集，則前兩個警告為輸出，但第三個是隱藏的。 以下是範例程式碼的組建輸出：  
  
**1 >------組建已開始：專案： CoreCheckExample，設定： Debug Win32--**  
**----**  
**1 > CoreCheckExample .cpp**  
**1 > CoreCheckExample. .vcxproj-> C:\Users\username\documents\visual studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample. .vcxproj-> C:\Users\username\documents\visual studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb （完整 PDB）**  
**c:\users\username\documents\visual studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp （6）：警告 C26494：變數 ' arr ' 為 uninitializ**  
**ed：一律初始化物件。（類型. 5： https://go.microsoft.com/fwlink/p/?Link**  
**識別碼 = 620421）**  
**c:\users\username\documents\visual studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp （7）：警告 C26485：運算式 ' arr '：沒有陣列**  
**指標衰減。（範圍3： https://go.microsoft.com/fwlink/p/?LinkID=620415)**  
= = = = = = = = = =**組建：1成功、0失敗、0最新、0略過 =** = = = = = = = = = =C++核心指導方針可協助您撰寫更好且更安全的程式碼。 不過，如果您有不應套用規則或設定檔的實例，則可以直接在程式碼中將它隱藏。 您可以使用 `gsl::suppress` 屬性，讓C++核心檢查無法偵測和報告下列程式碼區塊中的任何規則違規。 您可以標記個別語句，以隱藏特定規則。 您甚至可以藉由撰寫 `[[gsl::suppress(bounds)]]` 而不包含特定的規則編號來隱藏整個界限設定檔。  
  
## <a name="use-the-guideline-support-library"></a>使用指導方針支援程式庫  
 CppCoreCheck NuGet 套件也會安裝套件，其中包含 Microsoft 的指導方針支援程式庫（GSL）的實施。 GSL 也以獨立形式提供，位於[http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl)。 如果您想要遵循核心指導方針，此程式庫會很有説明。 GSL 包含的定義可讓您以更安全的替代專案來取代容易出錯的結構。 例如，您可以使用 `span<T>` 類型來取代一組 `T*, length` 的參數。 GSL 是開放原始碼，因此如果您想要查看程式庫來源、批註或參與，可以在[https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)找到專案。
