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
use fragment in MainActivity, replace TextView
```
<fragment android:id=@+/blank_fragment" class="com..BlankFragment" android:layout_width="wrap_content"
tools:layout="@layout/fragment_blank"/>
```
######Explore the FragmentTransaction class
create placeholder, do not need to add class prop here.  
activity_main.xml
```
<FrameLayout android:id="@+id/fragment_container" />
```

java code to add this fragment
```
BlankFragment bf = new BlankFragment();
getSupportFragmentManager().beginTransaction().add(R.id.fragment_container,bf).commit();
```

remove fragment
```
getSupportFragmentManager().beginTransaction().remove(bf).commit();
```
######Add a fragment with Java
02:53  
add button (centerHorizontal,alignParentBottom)


######Remove a fragment with Java
use tag as reference
```
public static final String TAG ="KE_TAG"
```
add fragment use tag as third parameter
```
add(R.id.fragment_container,bf,TAG).commit();
```
delete fragment using findFragmentByTag
```
Fragment bf = getSupportFragmentManager().findFragmentByTag(TAG);
```
addToBackStack: remove when press back
```
beginTransaction().addToBackStack(null).add(R.id.fragment_container,bf,TAG).commit();
```
######The lifecycle of a fragment
resumed: visible and interactive  
paused: can be visible but without focus  
stopped: not visible
```
onAttach(save ref of containing activity)->onCreate(retrieve values from fragment)->onCreateView(get reference from layout->
onActivityCreated()->onStart()->onResume()...->onPause()->onStop()
onDestroyView()->onDestroy()->onDetach()
```
