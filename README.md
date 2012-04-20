#jQuery Twitter v1.0
====================

jQuery Twitter is a lightweight (2kb minified) and easy to use jQuery plugin that uses Twitter API to pull tweets from a user timeline.

Automatically format links and dates. You can show dates in absolute time (eg.: 04/20/2012 at 10h45) or relative time (eg.: 2 hours ago).

Dates are easily formatted for a better localization

##How to use:

Make sure to include jQuery in your page:

	<script src="//ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"></script>

Include **jQuery Twitter:**

	<script src="js/jquery.twitter.min.js"></script>

HTML markup (just an example, do as you want)

	<div class="tweet">
		<p></p>
		<p></p>
	</div>

Initialize **jQuery Twitter:**

	<script>
		$(function(){
			$.twitter('username', 2, function(data){
				$('.tweet').find('p').each(function(i){
					$(this).html(data[i].text).append('<span>' + data[i].time + '</span>');
				});
			});
		});
	</script>
	
##Callback:

Callback function passes a object as first parameter

	function(data){
		// data[index].text = Tweet
		// data[index].time = Time of tweet formated
		// data.length = Number of tweets returned
		// data.profile.avatar = User avatar
		// data.profile.followers = User followers count
		// data.profile.screen_name = User screen name
	}
	
##Usage:

	$.twitter(string username[, integer number_of_tweets], function callback[, object { options }]);
	
##Options:

<table>
	<tr>
		<td><strong>Option</strong></td>
		<td><strong>Default</strong></td>
		<td><strong>Type</strong></td>
		<td><strong>Description</strong></td>
	</tr>
	<tr>
		<td>timeSpan</td>
		<td>true</td>
		<td>Boolean</td>
		<td>Toggle time format between relative and absolute</td>
	</tr>
	<tr>
		<td>exclude_replies</td>
		<td>true</td>
		<td>Boolean</td>
		<td>Exclude direct replies from response</td>
	</tr>
	<tr>
		<td>time_format</td>
		<td>'%1 %0, %2 at %3'</td>
		<td>String</td>
		<td>Date/time format, %0 for day, %1 for month, %2 for year and %3 for hour (timeSpan option muste be <em>false</em>)</td>
	</tr>
	<tr>
		<td>less_than_a_min</td>
		<td>'less than a minute ago'</td>
		<td>String</td>
		<td>Less than a minute ago string for localization (only show if timeSpan is <em>true</em>)</td>
	</tr>
	<tr>
		<td>timespan_format</td>
		<td>'%0 %1 ago'</td>
		<td>String</td>
		<td>Date/time format, %0 for day, %1 for month, %2 for year and %3 for hour (timeSpan option muste be <em>true</em>)</td>
	</tr>
	<tr>
		<td>i18n_time</td>
		<td>['minute', 'hour', 'day']</td>
		<td>Array</td>
		<td>Time localization</td>
	</tr>
	<tr>
		<td>i18n_months</td>
		<td>['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']</td>
		<td>Array</td>
		<td>Months localization</td>
	</tr>
</table>