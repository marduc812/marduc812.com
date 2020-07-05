---
title: 'Working with large numbers [Android]'
author: ヤング marduc
type: post
date: 2016-06-12T13:56:26+00:00
url: /2016/06/12/working-with-large-numbers-android/
featured_image: /wp-content/uploads/2016/06/android-scientific-notation-100x50.jpg
factory_shortcodes_assets:
  - 'a:0:{}'
dsq_thread_id:
  - 4904412811
mashsb_timestamp:
  - 1587804884
mashsb_jsonshares:
  - '{"total":0,"error":{"facebook_error":"{"error":{"message":"(#12) share field is deprecated for versions v2.9 and higher","type":"OAuthException","code":12,"fbtrace_id":"AxAFNSJ7Yx0kiCdEWtAWvUv"}}"},"facebook_total":0}'
avada_post_views_count:
  - 512
categories:
  - Android
  - Tuts
tags:
  - Android
  - tutorial

---
A couple of years ago I developed an app that was click based with text and what you had to do was to collect as much money as possible in order to buy new buildings and things like that. What I didn&#8217;t think of (then) was that some time since you get such a big income<!--more--> the Integer wouldn&#8217;t be enough. Integer&#8217;s range starts from -2147483648 and goes up to 2147483647. This is because it is 32bit value, so it is 2

<sup>31</sup>. When you reach the maximum value this will take you back to minimum value, so money from 2 billions become -2 billions. In order to fix this I had to use a value that has really larger limit.

<table>
  <tr>
    <th>
      Variable
    </th>
    
    <th>
      Min. Value
    </th>
    
    <th>
      Max. Value
    </th>
  </tr>
  
  <tr>
    <td>
      Boolean
    </td>
    
    <td>
    </td>
    
    <td>
      1
    </td>
  </tr>
  
  <tr>
    <td>
      Byte
    </td>
    
    <td>
      -128
    </td>
    
    <td>
      127
    </td>
  </tr>
  
  <tr>
    <td>
      Short
    </td>
    
    <td>
      -32.768
    </td>
    
    <td>
      32.767
    </td>
  </tr>
  
  <tr>
    <td>
      Char
    </td>
    
    <td>
    </td>
    
    <td>
      65535
    </td>
  </tr>
  
  <tr>
    <td>
      Integer
    </td>
    
    <td>
      -2.147.483.648
    </td>
    
    <td>
      2.147.483.647
    </td>
  </tr>
  
  <tr>
    <td>
      Long
    </td>
    
    <td>
      -9.223.372.036.854.775.808
    </td>
    
    <td>
      9.223.372.036.854.775.807
    </td>
  </tr>
  
  <tr>
    <td>
      Float
    </td>
    
    <td>
      1.4E-45
    </td>
    
    <td>
      3.4028235E38
    </td>
  </tr>
  
  <tr>
    <td>
      Double
    </td>
    
    <td>
      4.9E-324
    </td>
    
    <td>
      1.7976931348623157E308
    </td>
  </tr>
</table>

So I decided to work with Double since it would be easier for me to display large numbers using E. I built a dummy project with 1 EditText to have an input, 1 Button and one TextView to see the result. So it looks something like this.

<img class="wp-image-730 aligncenter" src="http://localhost/wp-content/uploads/2016/06/scientnot1.png" alt="scientnot(1)" width="258" height="513" /> 

I won&#8217;t analyse the code behind the buttons or the EditText I will go straight to the formatting part. What I wanted to achieve is to have a number that if is smaller than 10.000.000 to appear normal and if it is larger than that to appear in form of E. Normally the Double would print 7 or 8 digits in front of the E but I only wanted to so I created a Method in order to format the numbers a bit. This method is called NumFormat and it takes a Double number as input and returns a String.

<pre class="brush: java; title: ; notranslate" title="">private String NumFormat(Double number) {
    double compare;
    String st_result;
    compare = 10000000;
    if (number&gt;compare)
    {
        DecimalFormat formatter = new DecimalFormat("0.###E0");
        st_result = formatter.format(number);
    }
    else
    {
        DecimalFormat simpler = new DecimalFormat("###");
        st_result = simpler.format(number);
    }
    return st_result;
}
</pre>

If number is smaller than the value I compare it to, I want is to format it like a normal Interger, without any decimal digits. but if is larger I want it to be formatted with 3 decimal digits in front of the power and the value of E. Now I will call this method in my Activity.

<pre class="brush: java; title: ; notranslate" title="">con.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        inputnum = input.getText().toString();
        number = Double.valueOf(inputnum);
        res.setText(NumFormat(number));
 }
});
</pre>

In order to test it I will use 3 different numbers and see how it will get formatted.

[<img class="alignnone size-full wp-image-731" src="http://localhost/wp-content/uploads/2016/06/scientnot2.png" alt="scientnot(2)" width="1200" height="500" srcset="http://localhost/wp-content/uploads/2016/06/scientnot2.png 1200w, http://localhost/wp-content/uploads/2016/06/scientnot2-300x125.png 300w, http://localhost/wp-content/uploads/2016/06/scientnot2-768x320.png 768w, http://localhost/wp-content/uploads/2016/06/scientnot2-1024x427.png 1024w, http://localhost/wp-content/uploads/2016/06/scientnot2-100x42.png 100w, http://localhost/wp-content/uploads/2016/06/scientnot2-862x359.png 862w" sizes="(max-width: 1200px) 100vw, 1200px" />][1]

If you want to learn more about formatting you can take a look at [this][2].

 [1]: http://localhost/wp-content/uploads/2016/06/scientnot2.png
 [2]: http://stackoverflow.com/a/2944856/3347882