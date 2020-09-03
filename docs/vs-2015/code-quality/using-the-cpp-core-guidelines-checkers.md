---
title: 使用 C++ Core Guidelines 檢查Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: fffa4cec6a2bd7a340b90776ac20dc486f28045b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "84173548"
---
# <a name="using-the-c-core-guidelines-checkers"></a>使用 C++ Core Guidelines 檢查工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ Core Guidelines 是一組可攜的指導方針、規則和最佳作法，說明如何在 c + + 專家和設計工具建立的 c + + 中撰寫程式碼。  Visual Studio 現在支援增益集套件，可為程式碼分析工具建立其他規則，以檢查您的程式碼是否符合 C++ Core Guidelines 和建議改進。  
  
## <a name="the-c-core-guidelines-project"></a>C++ Core Guidelines 專案  
 C++ Core Guidelines 是由 Bjarne Stroustrup 和其他人所建立，則是安全且有效地使用新式 c + + 的指南。 這些指導方針強調靜態型別安全和資源安全。 它們會識別如何消除或最小化語言中最容易出錯的部分，並建議如何以可靠的方式，讓您的程式碼更簡單且更有效率。 這些指導方針是由 Standard c + + 基礎所維護。 若要深入瞭解，請參閱檔集、 [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)，以及存取 [GitHub](https://github.com/isocpp/CppCoreGuidelines)上 C++ Core Guidelines 檔專案檔。  
  
 Microsoft 藉由使用 Nuget 套件，讓您可以新增至專案中的 C++ Core Check 程式碼分析規則集，以支援 C++ Core Guidelines 的工作。 封裝的名稱是 CppCoreCheck，而且可以在上取得 [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) 。 此套件要求您至少已安裝 Update 1 Visual Studio 2015。  
  
 套件也會安裝另一個套件作為相依性，僅限標頭的指導方針支援程式庫 (GSL) 。 GSL 也可在 GitHub 上取得 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) 。  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>在程式碼分析中啟用 C++ Core Check 指導方針  
 若要啟用 C++ Core Check 程式碼分析工具，請將 CppCoreCheck NuGet 套件安裝到您想要在 Visual Studio 內檢查的每個 c + + 專案。  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>將 CppCoreCheck 套件新增至您的專案  
  
1. 在 **方案總管**中，以滑鼠右鍵按一下以開啟您想要新增封裝之方案中專案的內容功能表。 選擇 [ **管理 Nuget 套件** ] 以開啟 **NuGet 封裝管理員**。  
  
2. 在 [ **NuGet 封裝管理員** ] 視窗中，搜尋 CppCoreCheck。  
  
    ![Nuget 封裝管理員視窗會顯示 CppCoreCheck 套件](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. 選取 CppCoreCheck 套件，然後選擇 [ **安裝** ] 按鈕，將規則加入至您的專案。  
  
   當您在專案上啟用程式碼分析時，NuGet 套件會將額外的 MSBuild .targets 檔案新增至您的專案。 這個 .targets 檔案會新增 C++ Core Check 規則，做為 Visual Studio 程式碼分析工具的額外擴充功能。  
  
   您可以在專案的 [**屬性頁**] 對話方塊的 [程式**代碼分析**] 區段中，選取 [**啟用組建的程式碼分析**] 核取方塊，以啟用專案的程式碼分析。  
  
   ![程式碼分析一般設定的屬性頁](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   C++ Core Check 規則會成為啟用程式碼分析時所執行之預設規則集的一部分。 因為 C++ Core Check 規則正在開發中，某些規則可能無法在所有程式碼上使用，但在開發期間可能會提供資訊。 這些規則會以實驗的形式發行。 您可以選擇是否要在專案的屬性中執行已發行或實驗性規則。  
  
   ![程式碼分析延伸模組設定的屬性頁](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   若要啟用或停用 C++ Core Check 規則集，請開啟專案的 [ **屬性頁** ] 對話方塊。 在 [設定 **屬性**] 下，展開 [程式  **代碼分析**， **擴充**功能]。 在 [ **啟用 C++ Core Check () ** ] 旁的下拉式清單控制項中，或 **啟用 C++ Core Check (實驗) **中，選擇 **[是]** 或 [ **否**]。 選擇 **[確定]** 或 [套用] 以儲存 **您的變更** 。  
  
## <a name="check-types-bounds-and-lifetimes"></a>檢查類型、界限和存留期  
 C++ Core Check 套件目前包含 [型別安全](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type)、 [界限安全性](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)和 [存留期安全](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) 設定檔的檢查程式。  
  
 以下是 C++ Core Check 規則可找到的問題類型範例：  
  
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
  
 此範例示範 C++ Core Check 規則可找到的一些警告：  
  
- C26494 是規則類型。5：一律初始化物件。  
  
- C26485 是規則界限。3：無陣列對指標的衰減。  
  
- C26481 是規則界限。1：請勿使用指標算術。 請改用 `span`。  
  
  當您編譯此程式碼時，如果已安裝並啟用 C++ Core Check 程式碼分析規則集，則前兩個警告會是輸出，但會隱藏第三個警告。 以下是範例程式碼的組建輸出：  
  
**1>------組建已開始：專案： CoreCheckExample，設定： Debug Win32--**  
**----**  
**1> CoreCheckExample .cpp**  
**1> CoreCheckExample. .vcxproj-> C:\Users\username\documents\visual studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1> CoreCheckExample. .vcxproj-> C:\Users\username\documents\visual studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (完整 PDB) **  
**c:\users\username\documents\visual studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6) ：警告 C26494：變數 ' arr ' 為 uninitializ**  
**教育.一律初始化物件。 (類型。5： HTTPs： \/ /go.microsoft.com/fwlink/p/?Link**  
**識別碼 = 620421) **  
**c:\users\username\documents\visual studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7) ： warning C26485： Expression ' arr '：無陣列**  
**指標衰減。 (界限。3： HTTPs： \/ /go.microsoft.com/fwlink/p/?LinkID=620415) **  
**========== 建置: 1 成功、0 失敗、0 最新狀態、0 略過 ==========** 

C++ Core Guidelines 可協助您撰寫更好且更安全的程式碼。 但是，如果您有不應套用規則或設定檔的實例，則可以輕鬆地直接在程式碼中加以隱藏。 您可以使用 `gsl::suppress` 屬性，讓 C++ Core Check 在下列程式碼區塊中，防止偵測和報告規則違規。 您可以標記個別語句，以隱藏特定規則。 您甚至可以在 `[[gsl::suppress(bounds)]]` 不包含特定規則號碼的情況下撰寫，來隱藏整個界限設定檔。  
  
## <a name="use-the-guideline-support-library"></a>使用指導支援程式庫  
 CppCoreCheck NuGet 套件也會安裝套件，其中包含 Microsoft 的指導方針支援程式庫 (GSL) 。 GSL 也可在獨立的表單中取得 [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl) 。 如果您想要遵循核心指導方針，此程式庫會很有説明。 GSL 包含的定義可讓您以更安全的替代方案取代容易出錯的結構。 例如，您可以使用類型來取代一組 `T*, length` 參數 `span<T>` 。 GSL 是開放原始碼，因此，如果您想要查看程式庫來源、批註或投稿，可以在中找到專案 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) 。
