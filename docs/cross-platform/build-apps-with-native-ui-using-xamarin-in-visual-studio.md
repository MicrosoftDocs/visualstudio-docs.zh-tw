---
title: 使用 Visual Studio 的 Xamarin 建置具有原生 UI 的應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 3d813226dfa79a65da85a2b17e54306d12a4ed09
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2018
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>使用 Visual Studio 的 Xamarin 建置具有原生 UI 的應用程式

大多數選擇 Xamarin 和 C# 來撰寫跨平台行動應用程式的開發人員都會使用 Xamarin.Forms。 Xamarin.Forms 可定義與 iOS、Android 及「通用 Windows 平台」(UWP) 中的原生控制項對應的使用者介面。 如需有關 Xamarin.Forms 的描述，請參閱[了解在 Visual Studio 中建置 Xamarin.Forms 應用程式的基本概念](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)一文。

針對存取每個平台的原生使用者介面 API，本文說明各種不同方法。 與 Xamarin.Forms 相比，使用原生 API 來運作是難度較高的方法，因為這需要對每個平台的極為熟悉。 其優點在於，您可以依據每個平台的特定長處和功能，量身打造使用者介面，同時仍共用基礎商務邏輯。

在您完成[設定和安裝](../cross-platform/setup-and-install.md)及[驗證您的 Xamarin 環境](../cross-platform/verify-your-xamarin-environment.md)中的步驟之後，本逐步解說將示範如何建置具有原生 UI 層的基本 Xamarin 應用程式。 使用原生 UI 時，共用程式碼會位於 .NET Standard 類別庫中，而個別平台專案會包含 UI 定義。 以下是您將建置並在 iOS 和 Android 手機及 Windows 10 Desktop 上執行 (從左到右) 的應用程式。
  
[![iOS、Android 及 Windows 上的 Xamarin 程式](../cross-platform/media/cross-plat-xamarin-build-1.png "跨平台 Xamarin 組建 1")](../cross-platform/media/cross-plat-xamarin-build-1-Large.png#lightbox)
  
您將會執行下列步驟來建置應用程式：  
  
- [設立方案](#solution)  
  
- [撰寫共用的資料服務程式碼](#dataservice)  
  
- [設計適用於 Android 的 UI](#Android)  

- [設計適用於 Windows 的 UI](#Windows)  
  
- [後續步驟](#next) (包括設計 iOS 使用者介面)
  
> [!TIP]
> 您可以在 [GitHub 上的 mobile-samples 儲存機制 (英文)](https://github.com/xamarin/mobile-samples/tree/master/Weather) 中找到本專案的完整原始程式碼。
>
> 如果問題持續存在或您遇到錯誤，請將問題張貼在 [forums.xamarin.com](http://forums.xamarin.com) 上。有許多問題都可透過更新至 Xamarin 所需的最新 SDK 來解決，如需相關說明，請參閱適用於每個平台的 [Xamarin 版本資訊](https://developer.xamarin.com/releases/) \(英文\)。    
  
> [!NOTE]
> Xamarin 的開發人員文件也提供兼具快速入門與深入探討章節的幾個逐步解說，列出如下。 在所有這些頁面上，請確定已選取 [Visual Studio]，以查看 Visual Studio 特定的逐步解說。  
>   
>  -   具有原生 UI 的 Xamarin 應用程式：  
>     -   [Hello, Android](/xamarin/android/get-started/hello-android/) (單一畫面的簡單應用程式)  
>     -   [Hello, Android 多重畫面](/xamarin/android/get-started/hello-android-multiscreen/) (可瀏覽不同畫面的應用程式)  
>     -   [Android Fragment 逐步解說](/xamarin/android/platform/fragments/fragments/implementing-with-fragments/walkthrough/) (用於主要/詳細資料畫面及其他項目)  
>     -   [Hello, iOS](/xamarin/ios/get-started/hello-iOS/)  
>     -   [Hello, iOS 多重畫面](/xamarin/ios/get-started/hello-iOS-multiscreen/) 

>  -   具有 Xamarin.Forms (共用 UI) 的 Xamarin 應用程式  
>     -   [Hello, Xamarin.Forms](/xamarin/xamarin-forms/get-started/hello-xamarin-forms/quickstart/)  
>     -   [嗨，Xamarin.Forms 多重畫面 (英文)](/xamarin/xamarin-forms/get-started/hello-xamarin-forms-multiscreen/)  
  
<a name="solution" />

##  <a name="set-up-your-solution"></a>設立方案  

針對建立共用 .NET Standard 程式庫的原生 UI 應用程式，Visual Studio 沒有適用的方案範本。 不過，從個別專案建置這類方案並不難。 下列步驟會使用適用於每種應用程式平台類型的專案及適用於共用程式碼的 .NET Standard 程式庫，來建立 Xamarin 方案。  
  
1.  在 Visual Studio 中，建立一個新的**類別庫 (.NET Standard)** 方案並命名為 **WeatherApp**。 尋找此範本的最簡單方式是選取左邊的 [Visual C#]，然後選取 [.NET Standard]： 

    ![建立 .NET Standard 方案](../cross-platform/media/cross-plat-xamarin-build-2.png "跨平台 Xamarin 組建 2")

    按一下 [確定] 之後，**WeatherApp** 方案就會包含一個名為 **WeatherApp**的單一專案。 

2.  如果您想要以 iOS 作為目標，請將 iOS 專案新增至方案中。 在 [方案總管] 中的方案名稱上按一下滑鼠右鍵，然後選取 [新增] 和 [新增專案]。  在 [新增專案] 對話方塊中，從左邊選取 [Visual C#]，然後選取 [iOS] 和 [通用]。 (如果找不到，您可能必須安裝 Xamarin 或啟用 Visual Studio 2017 功能，請參閱[設定和安裝](../cross-platform/setup-and-install.md))。在範本清單中，選取 [單一檢視應用程式 (iOS)]。 將它命名為 **WeatherApp.iOS**。

3.  如果您想要以 Android 作為目標，請將 Android 專案新增至方案中。 在 [新增專案] 對話方塊中，從左邊選取 [Visual C#]，然後選取 [Android]。 在範本清單中，選取 [空白應用程式 (Android)]。 將它命名為 **WeatherApp.Android**。 

4. 如果您想要以「通用 Windows 平台」作為目標，請在 [新增專案] 對話方塊中，從左邊選取 [Visual C#] 和 [Windows 通用]。 在範本清單中，選取 [空白應用程式 (通用 Windows)]，然後將它命名為 **WeatherApp.UWP**。
  
5. 針對每個應用程式專案 (iOS、Android 及 UWP)，在 [方案總管] 中的 [參考] 區段上按一下滑鼠右鍵，然後選取 [加入參考]。 在 [參考管理員] 對話方塊中，從左邊選取 [專案] 和 [方案]。 您將會看到方案中所有專案的清單，但不包括您正在管理參考的專案：

   ![設定對 .NET Standard 專案的參考](../cross-platform/media/cross-plat-xamarin-build-3.png "跨平台 Xamarin 組建 3")

   請勾選 **WeatherApp** 旁的核取方塊。 

   針對每個應用程式專案勾選此方塊之後，所有專案就會包含對 .NET Standard 程式庫的參考，而可以共用該程式庫中的程式碼。
  
6. 將 **Newtonsoft.Json** NuGet 套件新增至 .NET Standard 專案，您將使用此專案來處理從天氣資料服務擷取的資訊：  
  
    -   在 [方案總管] 中的 [WeatherApp] 專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。  
  
         在 [NuGet] 視窗中，選取 [瀏覽] 索引標籤，然後搜尋 **Newtonsoft**。  
  
    -   選取 **Newtonsoft.Json**。  
  
    -   請確認 [版本]  欄位設為 [最新穩定版]  。  
  
    -   按一下 [安裝] 。  
  
7.  重複步驟 6 以尋找並安裝 .NET Standard 專案中的 **Microsoft.CSharp** 套件。 必須要有此程式庫，才能使用 .NET Standard 程式庫中的 C# `dynamic` 資料類型。
  
8.  建置方案，並確認沒有任何建置錯誤。  
  
<a name="dataservice" />

## <a name="write-shared-data-service-code"></a>寫入共用的資料服務程式碼  

 **WeatherApp** 專案是 .NET Standard 程式庫。 您將在此專案中撰寫跨所有平台共用的程式碼。 由於每個應用程式專案都具有對 .NET Standard 程式庫的參考，因此 iOS、Android 及 UWP 應用程式套件都會隨附此程式庫。  
  
 下列步驟會將程式碼新增至 .NET Standard 程式庫，以存取和儲存來自該天氣服務的資料：  
  
1.  先在 [http://openweathermap.org/appid](http://openweathermap.org/appid)註冊免費的天氣 API 金鑰。 此 API 金鑰將可允許應用程式取得任何美國郵遞區號的天氣資料。 (這不適用於美國境外的郵遞區號)。
  
2.  以滑鼠右鍵按一下 **WeatherApp** 專案，然後選取 [新增] > [類別...]。在 [加入新項目]  對話方塊中，將檔案命名為 **Weather.cs**。 您將使用此類別儲存天氣資料服務的資料。  
  
3.  以下列程式碼取代整個 **Weather.cs** 的內容：  
  
    ```csharp  
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```  
  
4.  將其他類別新增至名為 **DataService.cs** 的 .NET Standard 專案。 您將使用此類別來處理來自天氣資料服務的 JSON 資料。  
  
5.  以下列程式碼取代整個 **DataService.cs** 的內容：  
  
    ```csharp  
    using System.Net.Http;  
    using System.Threading.Tasks;  
    using Newtonsoft.Json;  
  
    namespace WeatherApp  
    {  
        public class DataService  
        {  
            public static async Task<dynamic> getDataFromService(string queryString)  
            {  
                HttpClient client = new HttpClient();  
                var response = await client.GetAsync(queryString);  
  
                dynamic data = null;  
                if (response != null)  
                {  
                    string json = response.Content.ReadAsStringAsync().Result;  
                    data = JsonConvert.DeserializeObject(json);  
                }  
  
                return data;  
            }  
        }  
    }  
    ```  
  
6.  在名為 **Core.cs** 的 .NET Standard 程式庫中新增第三個類別。 您將使用此程式碼來組成含郵遞區號的查詢字串、呼叫天氣資料服務，然後填入 **Weather** 類別的執行個體。  
  
7.  以下列程式碼取代 **Core.cs** 的內容：  
  
    ```csharp  
    using System;  
    using System.Threading.Tasks;  
  
    namespace WeatherApp  
    {  
        public class Core  
        {  
            public static async Task<Weather> GetWeather(string zipCode)  
            {  
                //Sign up for a free API key at http://openweathermap.org/appid  
                string key = "YOUR API KEY HERE";  
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="  
                    + zipCode + ",us&appid=" + key + "&units=imperial";  

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }
  
                dynamic results = await DataService.GetDataFromService(queryString).ConfigureAwait(false);  
  
                if (results["weather"] != null)  
                {  
                    Weather weather = new Weather();  
                    weather.Title = (string)results["name"];                  
                    weather.Temperature = (string)results["main"]["temp"] + " F";  
                    weather.Wind = (string)results["wind"]["speed"] + " mph";                  
                    weather.Humidity = (string)results["main"]["humidity"] + " %";  
                    weather.Visibility = (string)results["weather"][0]["main"];  
  
                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);  
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);  
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);  
                    weather.Sunrise = sunrise.ToString() + " UTC";  
                    weather.Sunset = sunset.ToString() + " UTC";  
                    return weather;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
        }  
    }  
    ```  
  
8. 以您在步驟 1 中取得的 API 金鑰取代第一個出現的 *YOUR API KEY HERE*。 仍然需要用引號括住它！
  
9. 刪除 .NET Standard 程式庫中的 **MyClass.cs**，因為將不會用到它。  
  
10. 建置 **WeatherApp** 專案，以確保程式碼正確。  
  
<a name="Android" />

## <a name="design-ui-for-android"></a>設計適用於 Android 的 UI  

 現在，您可以設計使用者介面、將它連接到您的共用程式碼，然後執行應用程式。  
  
### <a name="design-the-look-and-feel-of-your-app"></a>設計應用程式的外觀與風格  
  
1.  在 [方案總管] 中，展開 [WeatherApp.Droid] > [資源] > [版面配置] 資料夾，然後開啟 **Main.axml**。 此命令會在視覺化設計工具中開啟檔案。 (如果出現 Java 相關錯誤，請參閱此[部落格文章](http://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9))。  
  
    > [!TIP]
    >  專案中還有許多其他檔案。 本文的範圍並未涵蓋探索這些檔案，但如果您想要更深入了解 Android 專案的結構，請參閱 Hello Android 文章的[第 2 部分：深度剖析](/xamarin/android/get-started/hello-android/hello-android-deepdive/)。  
  
2.  透過 [檢視] > [其他視窗] > [工具箱] 來開啟 [工具箱]。  
  
3.  從 **工具箱**將 **RelativeLayout** 控制項拖曳到設計工具內。 您將使用此控制項做為其他控制項的父容器。  
  
    > [!TIP]
    >  如果在任何時候配置似乎不正確地顯示，請儲存檔案，並在 [設計] 和 [來源] 索引標籤之間切換，以進行重新整理。  
  
4.  在 [屬性] 視窗中，將 [背景] 屬性 (在 [樣式] 群組中) 設為 `#545454`。  進入您正在為 **RelativeLayout**.設定背景的 [屬性] 視窗來進行確認。
  
5.  從 **工具箱**將 **TextView** 控制項拖曳到 **RelativeLayout** 控制項內。  
  
6.  在 [屬性] 視窗中，設定下列屬性。 (使用 [屬性] 視窗工具列中的排序按鈕將有助於依字母順序排序清單。)：  
  
    |屬性|值|  
    |--------------|-----------|  
    |**text**|**Search by Zip Code (依郵遞區號搜尋)**|  
    |**id**|`@+id/ZipCodeSearchLabel`|  
    |**layout_marginStart**|`10dp`|  
    |**textColor**|`@android:color/white`|  
    |**textStyle**|`bold`|  
  
    > [!TIP]
    >  請注意，有許多屬性不包含可供您選取之值的下拉式清單。  所以可能會很難知道指定的屬性要使用什麼字串值。 如需建議，請嘗試在 [R.attr](http://developer.android.com/reference/android/R.attr.html) 類別頁面中搜尋屬性的名稱。  
    >   
    >  此外，直接在網路上搜尋常被導向至 [http://stackoverflow.com/](http://stackoverflow.com/) 上的頁面；在其中，其他人已使用了相同的屬性。  
  
     基於參考的目的，如果您切換到 [原始碼] 檢視，應該會看到下列適用於此項目的程式碼：  
  
    ```xml  
    <TextView  
        android:text="Search by Zip Code"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:id="@+id/ZipCodeSearchLabel"  
        android:layout_marginStart="10dp"  
        android:textColor="@android:color/white"  
        android:textStyle="bold" />  
  
    ```  
  
7.  從 [工具箱] 中，將 [TextView] 控制項拖曳至 [RelativeLayout] 控制項，並將其放在 [ZipCodeSearchLabel] 控制項下方。 請將新控制項放在現有控制項的適當邊緣。 您可以將設計工具放大來協助您放置控制項。  
  
8. 在 [屬性]  視窗中，設定這些屬性：  
  
    |屬性|值|  
    |--------------|-----------|  
    |**文字**|**郵遞區號**|  
    |**id**|`@+id/ZipCodeLabel`|  
    |**layout_marginStart**|`10dp`|  
    |**layout_marginTop**|`6dp`|  
    |**textColor**|`@android:color/white`|  
  
    [原始碼] 檢視中的程式碼應該看起來如下：  
  
    ```xml  
    <TextView  
        android:text="Zip Code"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_below="@id/ZipCodeSearchLabel"  
        android:id="@+id/ZipCodeLabel"  
        android:layout_marginStart="10dp"
        android:layout_marginTop="6dp"  
        android:textColor="@android:color/white" />  
    ```  
  
9. 從 [工具箱] 中，將 [Number] 控制項拖曳至 [RelativeLayout]，並將它放在 [Zip Code]\(郵遞區號) 標籤下方。 接著，設定下列屬性：  
  
    |屬性|值|  
    |--------------|-----------|  
    |**id**|`@+id/zipCodeEntry`|  
    |**layout_marginStart**|`10dp`|  
    |**layout_marginBottom**|`10dp`|  
    |**width**|`165dp`|  
    |**textColor**|`@android:color/white`|  
  
    **Number** 控制項是使用者將輸入五位數美國郵遞區號的位置。 以下是與該控制項對應的標記：  
  
    ```xml  
    <EditText  
        android:inputType="number"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_below="@id/ZipCodeLabel"  
        android:id="@+id/zipCodeEntry"  
        android:layout_marginStart="10dp"  
        android:layout_marginBottom="10dp"  
        android:width="165dp"  
        android:textColor="@android:color/white" />  
    ```  
  
10. 從 [工具箱] 中，將 [按鈕] 拖曳至 [RelativeLayout] 控制項，並將它放在 [zipCodeEntry] 控制項右邊。 然後設定這些屬性：  
  
    |屬性|值|  
    |--------------|-----------|  
    |**id**|`@+id/weatherBtn`|  
    |**文字**|**獲知天氣**|  
    |**layout_marginStart**|`20dp`|  
    |**layout_alignBottom**|`@id/zipCodeEntry`|  
    |**width**|`165dp`|  
  
    ```xml  
    <Button
        android:text="Get Weather"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_toRightOf="@id/zipCodeEntry"  
        android:id="@+id/weatherBtn"  
        android:layout_marginStart="20dp"  
        android:layout_alignBottom="@id/zipCodeEntry"  
        android:width="165dp" />  
    ```  
  
11. 現在，您已具備足夠的知識，可使用 Android 設計工具來建置基本的 UI。 您也可以直接將標記新增至頁面的 Main.axml 檔案中來建置 UI。 若要以該方式建立其餘的 UI，請切換至設計工具中的 [原始碼] 檢視，然後將下列標記貼到 `</RelativeLayout>` 結束標籤的「下方」。 (它們必須在該標籤下方，因為這些元素「不」包含在 `RelativeLayout`中)。  
  
    ```xml  
    <TextView  
        android:text="Location"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/locationLabel"  
        android:layout_marginStart="10dp"  
        android:layout_marginTop="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/locationText"  
        android:layout_marginStart="20dp"  
        android:layout_marginBottom="10dp" />  
    <TextView  
        android:text="Temperature"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/tempLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/tempText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Wind Speed"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/windLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/windText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Humidity"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/humidtyLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/humidityText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Visibility"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/visibilityLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/visibilityText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Time of Sunrise"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunriseLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunriseText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Time of Sunset"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunsetLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunsetText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    ```  
  
12. 儲存檔案，然後切換至 [設計] 檢視。 您的 UI 會如下所示：  
  
     ![適用於 Android 應用程式的 UI](../cross-platform/media/xamarin_androidui.png "Xamarin_AndroidUI")  
  
13. 開啟 **MainActivity.cs**。 程式碼應該看起來如下：  
  
    ```  
    protected override void OnCreate (Bundle bundle)  
    {  
        base.OnCreate (bundle);  
  
        // Set our view from the "main" layout resource  
        SetContentView (Resource.Layout.Main);  
    }  
    ```  
  
14. 建置 Android 專案以檢查您的工作。 此建置程序會將控制項識別碼新增至 **Resource.Designer.cs** 檔案，讓您可以在程式碼中依名稱參考控制項。  
  
### <a name="consume-your-shared-code"></a>使用您的共用程式碼  
  
1.  在程式碼編輯器中開啟 **WeatherApp** 專案的 **MainActivity.cs** 檔案，並使用下列程式碼來取代它的內容。 此程式碼會呼叫您在共用程式碼中定義的 `GetWeather` 方法。 然後它會在應用程式的 UI 中，顯示從該方法擷取的資料。  
  
    ```csharp  
    using System;  
    using Android.App;  
    using Android.Widget;  
    using Android.OS;  
  
    namespace WeatherApp.Droid  
    {  
        [Activity(Label = "Sample Weather App", 
                  Theme = "@android:style/Theme.Material.Light", 
                  MainLauncher = true)]  
        public class MainActivity : Activity  
        {  
            protected override void OnCreate(Bundle bundle)  
            {  
                base.OnCreate(bundle);  
  
                SetContentView(Resource.Layout.Main);  
  
                Button button = FindViewById<Button>(Resource.Id.weatherBtn);  
  
                button.Click += Button_Click;  
            }  
  
            private async void Button_Click(object sender, EventArgs e)  
            {  
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);  
  
                if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
                {  
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;  
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;  
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;  
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;  
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;  
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;  
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;  
                }  
            }  
        }  
    }  
    ```  

    請注意，活動已具有淺色背景主題。
  
### <a name="run-the-app-and-see-how-it-looks"></a>執行應用程式並觀察其結果  
  
1.  在 [方案總管] 中，確定已將 **WeatherApp.Droid** 專案設為啟始專案。  
  
2.  選取適當的裝置或模擬器目標，然後按 F5 鍵以啟動應用程式。  

    > [!NOTE]
    > 如果 Visual Studio 指出 Android 專案找不到 Newtonsoft.Json 檔案，請將該 NuGet 套件新增至 Android 專案。 
  
3.  在裝置上或模擬器中，於編輯方塊中輸入有效的美國五位數郵遞區號，然後按 [Get Weather]\(獲知天氣)。 該地區的天氣資料隨即會顯示在控制項中。  
  
    [![Android 上的 Xamarin 應用程式](../cross-platform/media/cross-plat-xamarin-build-1-android.png "跨平台 Xamarin 組建 1 Android")](../cross-platform/media/cross-plat-xamarin-build-1-android-Large.png#lightbox)  
  
> [!TIP]
>  本專案的完整原始程式碼位於 [GitHub 上的 mobile-samples 存放庫 (英文)](https://github.com/xamarin/mobile-samples/tree/master/Weather) 中。  
  
<a name="Windows" /> 

## <a name="design-ui-for-windows"></a>設計適用於 Windows 的 UI

下一步是設計適用於 Windows 的使用者介面、將其連接到您的共用程式碼，然後執行應用程式。  
  
### <a name="design-the-look-and-feel-of-your-app"></a>設計應用程式的外觀與風格  

 設計 Xamarin 應用程式中原生 UWP 使用者介面的流程，與任何其他原生 UWP 應用程式一樣。 因此，這裡將不討論設計工具的使用。 如需詳細的討論，請參閱[使用 XAML 設計工具來建立 UI](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)。  
  
 取而代之的是，請開啟 **MainPage.xaml**，然後以下列標記取代整個 XAML 內容：   
  
```xaml  
<Page
    x:Class="WeatherApp.UWP.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.UWP"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

        <StackPanel HorizontalAlignment="Left" 
                    VerticalAlignment="Top" 
                    Height="40" Margin="10,0,0,0" Width="400">
            <TextBlock Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left" 
                    VerticalAlignment="Top" 
                    Height="120" Margin="10,40,0,0" Width="400" 
                    Background="#FF545454">

            <TextBlock Text="Search by Zip Code" TextWrapping="Wrap" 
                       HorizontalAlignment="Left" Margin="10,10,0,0"
                       Foreground="White" FontSize="18" FontWeight="Bold" />
            
            <TextBlock Text="Zip Code" TextWrapping="Wrap" 
                       Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>
            
            <StackPanel Orientation="Horizontal">

                <TextBox x:Name="zipCodeEntry" Text="" 
                         Margin="10,10,0,0" VerticalAlignment="Top" 
                         InputScope="Number" Width="165" />
                
                <Button x:Name="weatherBtn" Content="Get Weather" 
                        Foreground="White" Width="165" Margin="20,0,0,0" Height="60" 
                        Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>
        
        <StackPanel Margin="10,175,0,0">
            <StackPanel.Resources>
                <Style x:Key="commonText" TargetType="TextBlock">
                    <Setter Property="HorizontalAlignment" Value="Left" />
                    <Setter Property="VerticalAlignment" Value="Top" />
                    <Setter Property="TextWrapping" Value="Wrap" />
                </Style>
                
                <Style x:Key="labelText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="14" />
                    <Setter Property="Foreground" Value="#FFA8A8A8" />
                </Style>

                <Style x:Key="valueText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="18" />
                    <Setter Property="Margin" Value="10, 0, 0, 10" />
                </Style>
            </StackPanel.Resources>
            
            <TextBlock Text="Location" Style="{StaticResource labelText}" />
            <TextBlock x:Name="locationText" Style="{StaticResource valueText}" />

            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="tempText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Wind Speed" Style="{StaticResource labelText}" />
            <TextBlock x:Name="windText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Humidity" Style="{StaticResource labelText}" />
            <TextBlock x:Name="humidityText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="visibilityText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Time of Sunrise" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunriseText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Time of Sunset" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunsetText" Style="{StaticResource valueText}" />
        </StackPanel>
    </Grid>
</Page>
```  
  
### <a name="consume-your-shared-code"></a>使用您的共用程式碼  
  
在 **MainPage.xaml.cs** 程式碼後置檔案中，為按鈕新增下列事件處理常式： 
  
```csharp  
private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)  
{  
    if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
    {  
        Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
        locationText.Text = weather.Title;  
        tempText.Text = weather.Temperature;  
        windText.Text = weather.Wind;  
        visibilityText.Text = weather.Visibility;  
        humidityText.Text = weather.Humidity;  
        sunriseText.Text = weather.Sunrise;  
        sunsetText.Text = weather.Sunset;  

        weatherBtn.Content = "Search Again";  
    }  
}  
```  
  
此程式碼會呼叫您在共用程式碼中定義的 `GetWeather` 方法。 `GetWeather`與您在 Android 應用程式中呼叫的方法一樣。 此程式碼也會在您應用程式的 UI 控制項中，顯示該方法所擷取的資料。  
  
### <a name="run-the-app-and-see-how-it-looks"></a>執行應用程式並觀察其結果  
  
1.  在 [方案總管] 中，將 [WeatherApp.UWP] 專案設定為啟始專案。  

2.  在 [方案平台] 下拉式方塊中，選取 [x86]，然後選取 [本機電腦]，以將應用程式部署至 Windows 10 Desktop。
  
3.  按 F5 鍵以啟動應用程式。  
  
4.  在編輯方塊中輸入有效的五位數美國郵遞區號，然後按 [Get Weather]\(獲知天氣)。 該地區的天氣資料隨即會顯示在頁面上。  

    [![UWP 上的 Xamarin 應用程式](../cross-platform/media/cross-plat-xamarin-build-1-uwp.png "跨平台 Xamarin 組建 1 UWP")](../cross-platform/media/cross-plat-xamarin-build-1-uwp-Large.png#lightbox)  

> [!TIP]
>  本專案的完整原始程式碼位於 [GitHub 上的 mobile-samples 存放庫 (英文)](https://github.com/xamarin/mobile-samples/tree/master/Weather) 中。  

<a name="next" /> 

## <a name="next-steps"></a>後續步驟  

 **將適用於 iOS 的 UI 加入至方案**  
  
 加入適用於 iOS 的原生 UI 來延伸此範例。 若要在 iOS 上測試程式碼，您將需要連線至區域網路上已安裝 Xcode 和 Xamarin 的 Mac。 完成該動作之後，您就可以直接在 Visual Studio 中使用 iOS 設計工具。 如需完整的應用程式，請參閱 [GitHub 上的 mobile-samples 儲存機制 (英文)](https://github.com/xamarin/mobile-samples/tree/master/Weather)。  
  
 另請參閱 [Hello, iOS](/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?tabs=vswin) 逐步解說。   
  
 **將平台專屬的程式碼加入共用專案**  
  
 .NET Standard 程式庫中的共用程式碼是不區分平台的。 此程式庫只會編譯一次，並且會包含在每個平台專屬的應用程式套件中。 如果您想要撰寫共用程式碼，以使用條件式編譯來隔離平台專屬的程式碼，您可以使用「共用」專案。 如需詳細資訊，請參閱[程式碼共用選項](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/practical-code-sharing-strategies)。  
  
## <a name="see-also"></a>請參閱  

 [Xamarin 文件](http://docs.microsoft.com/xamarin)   
 [Windows 開發人員中心](https://dev.windows.com/en-us)   
 [Swift 與 C# 的快速參考海報](http://aka.ms/scposter)
