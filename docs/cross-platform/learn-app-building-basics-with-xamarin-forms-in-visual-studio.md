---
title: "了解在 Visual Studio 中建置 Xamarin.Forms 應用程式的基本概念 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2018
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.technology: vs-ide-mobile
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- xamarin
ms.openlocfilehash: 71470cd03844c7761afbd07c9d454214f5dc36ca
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>了解在 Visual Studio 中建置 Xamarin.Forms 應用程式的基本概念

在您完成 [Setup and install](../cross-platform/setup-and-install.md) 和 [Verify your Xamarin environment](../cross-platform/verify-your-xamarin-environment.md)中的步驟之後，本逐步解說會示範如何建立 Xamarin.Forms 基本應用程式 (如下所示)。 使用 Xamarin.Forms 時，您會一次將所有 UI 程式碼寫入 .NET Standard 類別庫。 接著，Xamarin 將會針對 iOS、Android 和通用 Windows 平台自動呈現原生 UI 控制項。 我們建議您使用這種方法 (而非使用共用專案)，因為 .NET Standard 程式庫只會包含所有目標平台皆支援的 .NET API，此外 Xamarin.Forms 亦可讓您跨平台共用 UI 程式碼。  
  
![Android、iOS 和 Windows 中的氣象應用程式範例](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
您將會執行下列步驟來建置應用程式：  
  
-   [設立方案](#solution)  
  
-   [寫入共用的資料服務程式碼](#dataservice)  
  
-   [開始寫入共用的 UI 程式碼](#uicode)  
  
-   [使用 Visual Studio Emulator for Android 測試您的應用程式。](#test)  
  
-   [完成 UI 使其具備跨平台的原生外觀與風格](#finish)  
  
> [!TIP]
> 您可以在 [GitHub 上的 xamarin-forms-samples 存放庫](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)找到本專案的完整原始程式碼。  
  
##  <a name="solution"></a> 設立方案  

下列步驟會建立 Xamarin.Forms 方案，其中包含共用程式碼的 .NET Standard 類別庫，以及兩個新增的 NuGet 套件。  
  
1.  在 Visual Studio 中，建立新的 [跨平台應用程式 (Xamarin.Forms)] 方案，並將其命名為 **WeatherApp**。 從左側清單中選取 [Visual C#] 和 [跨平台] 來尋找範本。  
  
     如果找不到，可能必須安裝 Xamarin，或是啟用 Visual Studio 2017 功能。請參閱[設定和安裝](../cross-platform/setup-and-install.md)。  
  
     ![建立新的空白應用程式 &#40;跨平台 Xamarin.Forms 應用程式&#41; 專案](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2.  按一下 [確定] 之後，將會有數個選項可供選取。 選擇 [空白應用程式]、[Xamarin.Forms] 及 [.NET Standard]：

     ![建立新的跨平台應用程式專案](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")
  
3.  按一下 [確定] 建立方案後，您會擁有數個個別專案：  
  
    -   **WeatherApp**：您將寫入跨平台共用之程式碼的 .NET Standard 程式庫，其中包括使用 Xamarin.Forms 的一般商務邏輯和 UI 程式碼。  
  
    -   **WeatherApp.Android**：包含原生 Android 程式碼的專案。 這會設為預設啟始專案。  
  
    -   **WeatherApp.iOS**：包含原生 iOS 程式碼的專案。  
  
    -   **WeatherApp.UWP**：包含 Windows 10 UWP 程式碼的專案。  
  
    > [!NOTE]
    >  您可以隨意刪除任何不屬於目標平台的專案。   
  
     您可在每個原生專案中存取對應平台的原生設計工具，並可以實作平台特定畫面和所需的功能。  
  
4.  將您方案中的 Xamarin.Forms NuGet 套件升級為最新的穩定版本，如下所示。 每次建立新的 Xamarin 方案時，我們都建議您進行此步驟：  
  
    -   選取 [工具] > [NuGet 封裝管理員] > [管理方案的 NuGet 封裝]。  
  
    -   選取 [更新] 索引標籤下方的 [Xamarin.Forms] 套件，並選取要更新方案中的所有專案 。 (注意：請不要核取 Xamarin.Android.Support 的任何更新)。  
  
    -   將 [版本]  欄位更新為可使用的 [最新穩定版]  。  
  
    -   按一下 [安裝] 。  
  
         ![更新 Xamarin.Forms NuGet 封裝](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")  
  
5.  將 **Newtonsoft.Json** NuGet 套件新增至 **WeatherApp**專案，您將使用此專案來處理從天氣資料服務擷取而來的資訊：  
  
    -   在 NuGet 套件管理員 (在步驟 4 後仍保持開啟) 中，選取 [瀏覽] 索引標籤，並搜尋 **Newtonsoft**。  
  
    -   選取 **Newtonsoft.Json**。  
  
    -   核取 **WeatherApp** 專案 (這是唯一一個必須安裝套件的專案)。  
  
    -   請確認 [版本]  欄位設為 [最新穩定版]  。  
  
    -   按一下 [安裝] 。  
  
    ![找出並安裝 Newtonsoft.Json NuGet 封裝](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
6.  重複步驟 5 以尋找並安裝 **Microsoft.Net.Http** 套件。  
  
7.  建置方案，並確認沒有任何建置錯誤。  
  
##  <a name="dataservice"></a> 寫入共用的資料服務程式碼  

您可以在 **WeatherApp** 專案中撰寫 .NET Standard 程式庫程式碼，進而跨所有平台共用。 系統會自動依據 iOS、Android 和 Windows 專案，將此程式庫包含在應用程式套件中。  
  
若要執行此範例，您必須先在 [http://openweathermap.org/appid](http://openweathermap.org/appid) \(英文\) 註冊免費 API 金鑰。  
  
下列步驟接著會將程式碼新增至 .NET Standard 程式庫，以存取並儲存該天氣服務的資料：  
  
1.  以滑鼠右鍵按一下 **WeatherApp** 專案，然後選取 [新增] > [類別...]。在 [加入新項目]  對話方塊中，將檔案命名為 **Weather.cs**。 您將使用此類別儲存天氣資料服務的資料。  
  
2.  以下列程式碼取代整個 **Weather.cs** 的內容：  
  
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
  
3.  將另一個名為 **DataService.cs** 的類別新增至 **WeatherApp** 專案，以使用該類別來處理天氣資料服務的 JSON 資料。  
  
4.  以下列程式碼取代整個 **DataService.cs** 的內容：  
  
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
  
5.  將第三個名為 **Core** 的類別新增至 **WeatherApp** 專案，您會將共用的商務邏輯置於該類別中。 此程式碼會組成具郵遞區號的查詢字串，呼叫天氣資料服務，然後填入 **Weather** 類別的執行個體。  
  
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
  
7.  建置 **WeatherApp** 程式庫專案，以確保程式碼正確。  
  
##  <a name="uicode"></a> 開始寫入共用的 UI 程式碼  

Xamarin.Forms 可讓您在 .NET Standard 程式庫中實作共用的 UI 程式碼。 在這些步驟中，您會將具按鈕的頁面新增至該專案，該按鈕的功能是使用由上一節新增的天氣資料服務程式碼所傳回的資料來更新頁面上的文字：  
  
1.  新增名為 **WeatherPage.cs** 的 [內容頁面]，方法是以滑鼠右鍵按一下 **WeatherApp** 專案，然後選取 [新增] > [新增項目]。在 [新增項目] 對話方塊中，選取 [內容頁面]。 請勿選取 [內容頁面 (C#)] 或 [內容檢視]。 將它命名為 **WeatherPage.cs**。  
  
     ![新增 Xamarin.Forms XAML 頁面](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")  
  
     Xamarin.Forms 是以 XAML 為基礎，因此這個步驟會建立 **WeatherPage.xaml** 檔案以及巢狀的程式碼後置檔案 **WeatherPage.xaml.cs**。 這可讓您透過 XAML 或程式碼產生 UI。 您需要針對這兩項作業，進行本逐步解說中的一些步驟。  
  
2.  若要將按鈕加入 WeatherPage 畫面，請使用下列項目取代 **WeatherPage.xaml** 的內容：  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
           x:Class="WeatherApp.WeatherPage"
           Title="Sample Weather App">  
      <Button x:Name="getWeatherBtn" 
              Text="Get Weather"
              Clicked="GetWeatherBtn_Clicked" />  
    </ContentPage>  
    ```  
  
     請注意，您必須使用 **x:Name** 屬性來定義按鈕名稱，才可從程式碼後置檔案中依名稱參考此按鈕。  
  
3.  若要新增按鈕 **Clicked** 事件的事件處理常式以更新按鈕文字，請以下列程式碼取代 **WeatherPage.xaml.cs** 的內容 (您可視需要自行將 "60601" 變更為其他郵遞區號)。  
  
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
  
                //Set the default binding to a default object for now  
                BindingContext = new Weather();  
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
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());  
    }  
    ```  
  
5.  建置 **WeatherApp** 專案，以確保程式碼正確。  
  
##  <a name="test"></a> 使用 Visual Studio Emulator for Android 測試您的應用程式。  

您現在可以準備執行應用程式！ 現在，我們先執行 Android 版本以確認應用程式可從氣象服務取得資料。 在稍後新增更多 UI 項目之後，您也會執行 iOS 和 UWP 版本。   
  
1.  以滑鼠右鍵按一下 [WeatherApp.Android] 專案，然後選取 [設定為啟始專案] 以將其設為啟始專案。  
  
2.  在 Visual Studio 工具列中，系統會將 **WeatherApp.Android** 列為目標專案。 選取其中一個 Android 模擬器進行偵錯，並按 **F5**。 建議您使用其中一個會在 Android 版 Visual Studio 模擬器中執行應用程式的 **VisualStudio** 模擬器選項。  
  
     ![選取 Android 模擬器偵錯目標](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")  
  
3.  在模擬器中啟動應用程式時，請按一下 [獲知天氣]  按鈕。 您應該會看到按鈕的文字更新為 **Chicago**，這就是從天氣資料服務擷取之資料的 *Title* 屬性。  
  
     ![點選按鈕之前和之後的氣象應用程式](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")  
  
##  <a name="finish"></a> 完成 UI 使其具備跨平台的原生外觀與風格  

Xamarin.Forms 可針對每個平台呈現原生的 UI 控制項，讓您的應用程式自動擁有原生的外觀與風格。 為了更清楚了解這項功能，讓我們先完成郵遞區號輸入欄位的 UI，並顯示從服務傳回的天氣資料。  
  
1.  以下列程式碼取代 **WeatherPage.xaml** 的內容。 依上述方式使用 **x:Name** 屬性來命名的每個項目，皆可以從程式碼中參考。 Xamarin.Forms 也有提供數個[配置選項](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) \(英文\) (xamarin.com)。 在這裡，WeatherPage 是使用 [Grid](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) \(英文\) (xamarin.com) 和 [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) \(英文\) (xamarin.com)。  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
                 x:Class="WeatherApp.WeatherPage"
                 Title="Sample Weather App">

        <ContentPage.Resources>
            <ResourceDictionary>
                <Style x:Key="labelStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Small" />
                    <Setter Property="TextColor" Value="#404040" />
                </Style>
                <Style x:Key="fieldStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Medium" />
                    <Setter Property="Margin" Value="10,0,0,0" />
                </Style>
            </ResourceDictionary>
        </ContentPage.Resources>

        <StackLayout>
            <Grid BackgroundColor="#545454" Padding="10, 10, 10, 10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>

                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto" />
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
            
                <Label Text="Search by Zip Code" 
                       Grid.Row="0" Grid.Column="0" Grid.ColumnSpan="3"
                       HorizontalOptions="Center"
                       TextColor="White" FontAttributes="Bold" FontSize="Medium" />
            
                <Label x:Name="zipCodeLabel" Text="Zip Code:" 
                       Grid.Row="1" Grid.Column="0"
                       VerticalOptions="Center"
                       Style="{StaticResource labelStyle}"
                       TextColor="#C0C0C0" />
            
                <Entry x:Name="zipCodeEntry"
                       Grid.Row="1" Grid.Column="1"
                       VerticalOptions="Center"
                       Margin="5,0"
                       BackgroundColor="DarkGray"
                       TextColor="White" />
            
                <Button x:Name="getWeatherBtn" Text="Get Weather" 
                        Grid.Row="1" Grid.Column="2"
                        HorizontalOptions="Center"
                        VerticalOptions="Center"
                        BorderWidth="1"
                        BorderColor="White"
                        BackgroundColor="DarkGray"
                        TextColor="White"
                        Clicked="GetWeatherBtn_Clicked" />
            </Grid>

            <ScrollView VerticalOptions="FillAndExpand">
                <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
                    <Label Text="Location" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Temperature" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Temperature}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Humidity" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Humidity}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Visibility" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Visibility}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunrise}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunset}" Style="{StaticResource fieldStyle}" />
                </StackLayout>
            </ScrollView>
        </StackLayout>
    </ContentPage>  
     ```  
  
     雖然未在此示範，您可以使用 **OnPlatform** 標記來選取目前執行應用程式之平台專屬的屬性值 (請參閱[基本 XAML 語法](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) \(英文\) (xamarin.com))。 在程式碼後置檔案中，您可以使用 [Device.OnPlatform API](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) 來達到相同的目的。  
  
2.  以下列程式碼取代 **WeatherPage.xaml.cs**中的 **GetWeatherBtn_Clicked** 事件處理常式。 此程式碼會驗證項目欄位中是否有郵遞區號，擷取該郵遞區號的資料，將整個頁面的繫結內容設定為產生的 **Weather** 執行個體，然後將按鈕的文字設為「再次搜尋」。 請注意，UI 中的每個標籤都會繫結至 **Weather** 類別的屬性，因此當您將畫面的繫結內容設定至 **Weather** 執行個體時，就會自動更新那些標籤。  
  
    ```csharp  
    private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
    {  
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
        {  
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
            BindingContext = weather;  
            getWeatherBtn.Text = "Search Again";  
        }  
    }  
    ```  
  
3.  在 Android、iOS 和 Windows 這三個平台上執行應用程式：以滑鼠右鍵按一下適當的專案，選取 [設定為啟始專案]，然後在裝置上或模擬器中啟動應用程式。 輸入有效的美國五位數郵遞區號，然後按 [Get Weather] 按鈕，以顯示如下所示該區域的天氣資料。 針對 iOS 專案，您必須將 Visual Studio 連線至您網路上的 Mac OS X 電腦。  
  
     ![Android、iOS 和 Windows Phone 中的氣象應用程式範例](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
本專案的完整原始程式碼位於 [GitHub 上的 xamarin-forms-samples 存放庫](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)。