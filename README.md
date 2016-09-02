#### labuiandroidappfragapi
######Understanding frag
basic steps:
- create a java class extending fragment
- create XML file
- add fragment to an activity
- inflate layout
######Create an app with a fragment
create a basic activity.  
tick use a fragment  
activity_main.xml->content_main.xml->fragment_main.xml  
in content_main.xml,
```
andriod:name="com....MainActivityFragment"
```
#####2. Display Fragments in Activities
######Create a fragment class and layout

create an empty activity.Add a new fragment.Create layout XML but not include fragment factory methods and interface cb.  
memorize the params:
```
public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInsanceState){
  return inflater.inflate(R.layout.fragment_name,container,false);
}
```
some changes:  
FrameLayout->RelativeLayout
```
android:background="@android:color/holo_blue_light"
```
other settings
```
android:layout_centerInParent="true"
android:textSize="24dp"
```
