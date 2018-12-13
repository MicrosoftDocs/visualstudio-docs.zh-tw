---
title: 了解 Xamarin.Forms 應用程式建置基本概念
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 0cbc20bd714cabf9747145c114abfaa58a2e52a6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058320"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>了解在 Visual Studio 中建置 Xamarin.Forms 應用程式的基本概念
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


在您完成 [Setup and install](../cross-platform/setup-and-install.md) 和 [Verify your Xamarin environment](../cross-platform/verify-your-xamarin-environment.md)中的步驟之後，本逐步解說會示範如何建立 Xamarin.Forms 基本應用程式 (如下所示)。 使用 Xamarin.Forms 時，您可以一次將所有 UI 程式碼寫入可攜式類別庫 (PCL)。 接著，Xamarin 即可針對 iOS、Android 和 Windows 平台自動呈現原生 UI 控制項。 我們建議您使用這種方法：只有使用支援所有目標平台的 .NET API，PCL 選項才能達到最佳支援效果，此外 Xamarin.Forms 亦可讓您跨平台共用 UI 程式碼。

 ![Android、iOS 和 Windows Phone 中的氣象應用程式範例](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

 您將會執行下列步驟來建置應用程式：

-   [設立方案](#solution)

-   [寫入共用的資料服務程式碼](#dataservice)

-   [開始寫入共用的 UI 程式碼](#uicode)

-   [使用 Visual Studio Emulator for Android 測試您的應用程式。](#test)

-   [完成 UI 使其具備跨平台的原生外觀與風格](#finish)

> [!TIP]
>  您可以在 [GitHub 上的 xamarin-forms-samples 存放庫](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)找到本專案的完整原始程式碼。

##  <a name="solution"></a> 設立方案
 下列步驟會建立 Xamarin.Forms 方案，其中包含共用程式碼的 PCL 和兩個已加入的 NuGet 套件。

1.  在 Visual Studio 中，建立新的 **空白應用程式 (Xamarin.Forms 可攜式)** 方案，並將其命名為 **WeatherApp**。 您可以在搜尋欄位中輸入 **Xamarin.Forms** ，輕鬆找到這個範本。

     如果找不到，則可能必須安裝 Xamarin，或是啟用 Visual Studio 2015 功能，請參閱[設定與安裝](../cross-platform/setup-and-install.md)。

     ![建立新的空白應用程式 &#40;Xamarin.Forms 可攜式&#41; 專案](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2.  按一下 [確定] 建立解決方案後，您會擁有數個個別專案：

    -   **WeatherApp (可攜式)**：您會將跨平台共用的程式碼寫入此 PCL，包括搭配 Xamarin.Forms 使用的一般商務邏輯和 UI 程式碼。

    -   **WeatherApp.Droid**：包含原生 Android 程式碼的專案。 這會設為預設啟始專案。

    -   **WeatherApp.iOS**：包含原生 iOS 程式碼的專案。

    -   **WeatherApp.UWP**：包含 Windows 10 UWP 程式碼的專案。

    -   **WeatherApp.Windows (Windows 8.1)**：包含原生 Windows 8.1 程式碼的專案。

    -   **WeatherApp.WinPhone (Windows Phone 8.1)**：包含原生 Windows Phone 程式碼的專案。

    > [!NOTE]
    >  您可以隨意刪除任何不屬於目標平台的專案。 就本逐步解說的目的而言，我們會參考 Android、iOS 和 Windows Phone 8.1 專案。 UWP 和 Windows 8.1 專案的使用方式與 Windows Phone 8.1 專案十分相似。

     您可在每個原生專案中存取對應平台的原生設計工具，並可以實作平台特定畫面和所需的功能。

3.  將您方案中的 Xamarin.Forms NuGet 套件升級為最新的穩定版本，如下所示。 每次建立新的 Xamarin 方案時，我們都建議您進行此步驟：

    -   選取 [工具] > [NuGet 封裝管理員] > [管理方案的 NuGet 封裝]。

    -   核取 [更新]  索引標籤下方的 **Xamarin.Forms** 更新，並核取要更新方案中的所有專案 。 (注意：請不要核取 Xamarin.Android.Support 的任何更新)。

    -   將 [版本]  欄位更新為可使用的 [最新穩定版]  。

    -   按一下 [更新] 。

         ![更新 Xamarin.Forms NuGet 封裝](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

4.  將 **Newtonsoft.Json** 和 NuGet 套件新增至 PCL 專案，您將使用此專案來處理從天氣資料服務擷取而來的資訊：

    -   在 NuGet 套件管理員 (在步驟 3 後仍保持開啟) 中，選取 [瀏覽]  索引標籤，並搜尋 **Newtonsoft**。

    -   選取 **Newtonsoft.Json**。

    -   核取 **WeatherApp** 專案 (這是唯一一個必須安裝套件的專案)。

    -   請確認 [版本]  欄位設為 [最新穩定版]  。

    -   按一下 [安裝] 。

    -   ![找出並安裝 Newtonsoft.Json NuGet 封裝](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

5.  重複步驟 4 以尋找並安裝 **Microsoft.Net.Http** 套件。

6.  建置方案，並確認沒有任何建置錯誤。

##  <a name="dataservice"></a> 寫入共用的資料服務程式碼
 您可以在 **WeatherApp (可攜式)** 專案中撰寫可攜式類別庫 (PCL) 程式碼，進而跨所有平台共用。 系統會自動依據 iOS、Android 和 Windows Phone 專案，將 PCL 包含在應用程式套件中。

 若要執行此範例，您必須先在 [http://openweathermap.org/appid](http://openweathermap.org/appid) 註冊免費的 API 金鑰。

 下列步驟會將程式碼新增至 PCL 以存取並儲存天氣服務的資料：

1.  以滑鼠右鍵按一下 **WeatherApp** 專案，然後選取 [新增] > [類別...]。 在 [加入新項目]  對話方塊中，將檔案命名為 **Weather.cs**。 您將使用此類別儲存天氣資料服務的資料。

2.  以下列程式碼取代整個 **Weather.cs** 的內容：

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            public string Title { get; set; }
            public string Temperature { get; set; }
            public string Wind { get; set; }
            public string Humidity { get; set; }
            public string Visibility { get; set; }
            public string Sunrise { get; set; }
            public string Sunset { get; set; }

            public Weather()
            {
                //Because labels bind to these values, set them to an empty string to
                //ensure that the label appears on all platforms by default.
                this.Title = " ";
                this.Temperature = " ";
                this.Wind = " ";
                this.Humidity = " ";
                this.Visibility = " ";
                this.Sunrise = " ";
                this.Sunset = " ";
            }
        }
    }
    ```

3.  將另一個類別加入名為 **DataService.cs** 的 PCL 專案中，以使用該專案來處理天氣資料服務的 JSON 資料。

4.  以下列程式碼取代整個 **DataService.cs** 的內容：

    ```csharp
    using System.Threading.Tasks;
    using Newtonsoft.Json;
    using System.Net.Http;

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

5.  將第三個類別新增至名為 **Core** 的 PCL 中，您會在其中放置共用商務邏輯，例如使用郵遞區號形成查詢字串，接著呼叫天氣資料服務，然後填入 **Weather** 類別執行個體的邏輯。

6.  以下列項目取代 **Core.cs** 的內容。

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
                string key = "YOUR KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

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

7.  建置 **WeatherApp** PCL 專案，以確保程式碼正確。

##  <a name="uicode"></a> 開始寫入共用的 UI 程式碼
 Xamarin.Forms 可讓您在 PCL 中實作共用的 UI 程式碼。 在這些步驟中，您會將含按鈕的畫面加入 PCL 中，其會使用上一節加入的天氣資料服務程式碼所傳回的資料來更新它的文字：

1.  新增名為 **WeatherPage.cs** 的 [Forms Xaml 頁面]，方法是以滑鼠右鍵按一下 **WeatherApp** 專案，然後選取 [新增] > [新項目...]。在 [加入新項目]  對話方塊中，搜尋「表單」，選取 [表單 Xaml 頁面] ，並將其命名為 **WeatherPage.cs**。

     Xamarin.Forms 是以 XAML 為基礎，因此這個步驟會建立 **WeatherPage.xaml** 檔案以及巢狀的程式碼後置檔案 **WeatherPage.xaml.cs**。 這可讓您透過 XAML 或程式碼產生 UI。 您需要針對這兩項作業，進行本逐步解說中的一些步驟。

     ![新增 Xamarin.Forms XAML 頁面](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

2.  若要將按鈕加入 WeatherPage 畫面，請使用下列項目取代 WeatherPage.xaml 的內容：

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage">
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>
    </ContentPage>
    ```

     請注意，您必須使用 **x:Name** 屬性來定義按鈕名稱，才可從程式碼後置檔案中依名稱參考此按鈕。

3.  若要加入按鈕 **點選** 事件的事件處理常式以更新按鈕文字，請以下列程式碼取代 **WeatherPage.xaml.cs** 的內容 (您可視需要自行將 “60601” 變更為其他郵遞區號)。

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace WeatherApp
    {
        public partial class WeatherPage: ContentPage
        {
            public WeatherPage()
            {
                InitializeComponent();
                this.Title = "Sample Weather App";
                getWeatherBtn.Clicked += GetWeatherBtn_Clicked;

                //Set the default binding to a default object for now
                this.BindingContext = new Weather();
            }

            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
            {
                Weather weather = await Core.GetWeather("60601");
                getWeatherBtn.Text = weather.Title;
            }
        }
    }
    ```

4.  若要將 **WeatherPage** 作為應用程式啟動時的第一個開啟畫面，請以下列程式碼取代 **App.cs** 中的預設建構函式：

    ```csharp
    public App()
    {
        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5.  建置 WeatherApp PCL 專案，以確保程式碼正確。

##  <a name="test"></a> 使用 Visual Studio Emulator for Android 測試您的應用程式。
 您現在可以準備執行應用程式！ 現在，我們先執行 Android 版本以確認應用程式可從氣象服務取得資料。 您可在稍後加入更多 UI 項目之後，再執行 iOS 和 Windows Phone 版本 。 (注意：如果您是在 Windows 7 上執行 Visual Studio，請遵循相同的步驟，但改為使用 Xamarin Player)。

1.  以滑鼠右鍵按一下 **WeatherApp.Droid** 專案，然後選取 [設定為啟始專案] ，以將其設為啟始專案。

2.  在 Visual Studio 工具列中，即會將 **WeatherApp.Droid** 列為目標專案。 選取其中一個 Android 模擬器進行偵錯，並按 **F5**。 建議您使用 **VS 模擬器** 的其中一個選項，以 Android 版 Visual Studio 模擬器選項執行應用程式。

     ![選取 VS 模擬器偵錯目標](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

3.  在模擬器中啟動應用程式時，請按一下 [獲知天氣]  按鈕。 您應該會看到按鈕的文字更新為 **芝加哥，IL**，即為從天氣資料服務擷取的資料 *Title* 屬性。

     ![點選按鈕之前和之後的氣象應用程式](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

##  <a name="finish"></a> 完成 UI 使其具備跨平台的原生外觀與風格
 Xamarin.Forms 可針對每個平台呈現原生的 UI 控制項，讓您的應用程式自動擁有原生的外觀與風格。 為了更清楚了解這項功能，讓我們先完成郵遞區號輸入欄位的 UI，並顯示從服務傳回的天氣資料。

1. 以下列程式碼取代 **WeatherPage.xaml** 的內容。 請務必如上所述使用 **x:Name** 屬性來命名每個項目，才可從程式碼中參考這些項目。 Xamarin.Forms 也有提供一些 [版面配置選項](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com)；這裡的 WeatherPage 是使用 [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com)。

   ```xaml
   <?xml version="1.0" encoding="utf-8" ?>
   <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
          xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
          x:Class="WeatherApp.WeatherPage">

     <ContentPage.Resources>
       <ResourceDictionary>
         <Style x:Key="labelStyle" TargetType="Label">
           <Setter Property="TextColor" Value="#a8a8a8" />
           <Setter Property="FontSize" Value="Small" />
         </Style>
         <Style x:Key="fieldStyle" TargetType="Label">
           <Setter Property="TextColor">
             <OnPlatform x:TypeArguments="Color" iOS="Black" Android="White" WinPhone="White" />
           </Setter>
           <Setter Property="FontSize" Value="Medium" />
         </Style>
         <Style x:Key="fieldView" TargetType="ContentView">
           <Setter Property="Padding" Value="10,0,0,0" />
         </Style>
       </ResourceDictionary>
     </ContentPage.Resources>

     <ContentPage.Content>
       <ScrollView>
         <StackLayout>
           <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand"
                 BackgroundColor="#545454">
             <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
               <Label Text="Search by Zip Code" TextColor="White" FontAttributes="Bold"
                   FontSize="Medium" />
               <Label x:Name="zipCodeLabel" Text="Zip Code" Style="{StaticResource labelStyle}" />
               <Entry x:Name="zipCodeEntry" />
             </StackLayout>
             <StackLayout Padding="0,0,0,10" VerticalOptions="End">
               <Button x:Name="getWeatherBtn" Text="Get Weather" WidthRequest="185" BorderWidth="1" >
                 <!-- Set iOS colors; use defaults on other platforms -->
                 <Button.TextColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.TextColor>
                 <Button.BorderColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.BorderColor>
               </Button>
             </StackLayout>
           </StackLayout>
           <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
             <Label Text="Location" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Temperature" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="tempLabel" Text="{Binding Temperature}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="windLabel" Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Humidity" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="humidityLabel" Text="{Binding Humidity}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Visibility" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="visibilitylabel" Text="{Binding Visibility}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunriseLabel" Text="{Binding Sunrise}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunsetLabel" Text="{Binding Sunset}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
           </StackLayout>
         </StackLayout>
       </ScrollView>
     </ContentPage.Content>
   </ContentPage>
   ```

    請注意 **OnPlatform** 標記在 Xamarin.Forms 中的使用方式。 **OnPlatform** 標記會選取應用程式目前執行所在平台專屬的屬性值 (請參閱 [External XAML Syntax](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) (xamarin.com)。 我們在這裡使用它來設定資料欄位不同的文字色彩：在 Android 和 Windows Phone、 iOS 則為黑色上的白色。 您可以針對任何屬性與資料類型使用 **OnPlatform** ，以在 XAML 的任意位置進行平台專屬的調整。 在程式碼後置檔案中，您可以使用 [Device.OnPlatform API](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) 來達到相同的目的。

2. 以下列程式碼取代 **WeatherPage.xaml.cs**中的 **GetWeatherBtn_Clicked** 事件處理常式。 此程式碼會驗證項目欄位中是否有郵遞區號、擷取該郵遞區號的資料、將整個畫面的繫結內容設定為產生的 Weather 執行個體，然後將按鈕的文字設為「再次搜尋」。 請注意，UI 中的每個標籤會繫結至 Weather 類別屬性，因此當您將畫面的繫結內容設定為 **Weather** 執行個體時，就會自動更新這些標籤。

   ```csharp
   private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
   {
       if (!String.IsNullOrEmpty(zipCodeEntry.Text))
       {
           Weather weather = await Core.GetWeather(zipCodeEntry.Text);
           this.BindingContext = weather;
           getWeatherBtn.Text = "Search Again";
       }
   }
   ```

3. 在 Android、iOS 和 Windows Phone 這三個平台上執行應用程式：以滑鼠右鍵按一下適當的專案，選取 [設定為啟始專案]，然後在裝置上或模擬器中啟動應用程式。 輸入有效的美國郵遞區號 (例如 60601)，然後按 [獲知天氣] 按鈕，即可顯示該區域的天氣資料，如下所示。 若是 iOS 專案，您就必須將 Visual Studio 連線至您網路上的 Mac OS X 電腦。

    ![Android、iOS 和 Windows Phone 中的氣象應用程式範例](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

   本專案的完整原始程式碼位於 [GitHub 上的 xamarin-forms-samples 存放庫](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)。
