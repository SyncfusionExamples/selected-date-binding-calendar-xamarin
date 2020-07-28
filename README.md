# How to initialize the selected date in Xamarin.Forms Calendar (SfCalendar)

Initially, the calendar is loaded with the current day as selected date and you can initialize the calendar with specific date by using SelectedDate property in SfCalendar.

You can also refer the following article.

https://www.syncfusion.com/kb/11799/how-to-programatically-change-the-selected-date-in-xamarin-forms-calendar-sfcalendar

**STEP 1:** Create a ViewModel class and add a SelectedDate property with specific date.

``` c#
public class ViewModel : INotifyPropertyChanged
{
            public event PropertyChangedEventHandler PropertyChanged;
 
            private DateTime selectedDate = DateTime.Now.AddDays(5);
 
            public DateTime SelectedDate
            {
                get
                {
                    return this.selectedDate;
                }
                set
                {
                    this.selectedDate = value;
                    this.OnPropertyChanged("SelectedDate");
                }
            }
 
            public ViewModel()
            {
            }
 
            private void OnPropertyChanged(string propertyName)
            {
                this.PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
            }
}
```
**STEP 2:** Bind the SelectedDate ViewModel property to the SelectedDate property in SfCalendar.

``` xml
<calendar:SfCalendar x:Name="calendar"
                             DataSource="{Binding Appointments}"
                             SelectedDate="{Binding SelectedDate}">
        <calendar:SfCalendar.BindingContext>
            <local:ViewModel/>
        </calendar:SfCalendar.BindingContext>
</calendar:SfCalendar>
```
**Output**

![SelectedDateCalendar](https://github.com/SyncfusionExamples/selected-date-binding-calendar-xamarin/blob/master/ScreenShot/SelectedDateCalendar.png)
