<!-- METHOD-TYPE: REDCap Core -->
<!-- REDCap-Version: 15.0.20 -->

# REDCap::getGroupNames()

REDCap Developer Tools:
Documentation for Plugins, Hooks, & External Modules
REDCap Version 15.0.20
WARNING: Hooks will not work yet without the Hook Functions file!
In order to utilize REDCap hooks, you must create your Hook Functions PHP file on your web server, and then provide the full path to that file on the General Configuration page of the Control Center.
if(window.ExternalModules === undefined){
		window.ExternalModules = {}
	}

	window.ExternalModules.moduleDependentRequest = function(url, action){
		$.get(url, function(response){
			try{
				response = JSON.parse(response)
				action(response)
			}
			catch(e){
				if(response.startsWith('<!DOCTYPE')){
					console.error('An unexpected response was returned from ' + url)
					/**
					 * Assume the login page is being returned per:
					 * https://redcap.vumc.org/community/post.php?id=138578
					 */
					return
				}

				// Escape the response to prevent injection
				response = $('<div/>').text(response).html()
				
				simpleDialog(
					"<p>The module mentioned in the error below is preventing REDCap from working properly.  It is recommended to disable this module until it can be updated to avoid this error:<pre style='max-height: 50vh; white-space: pre-wrap;'>" + response + "",
					"Error",
					'module-error-dialog',
					1000
				)
			}
		})
	}

if(typeof lang=='undefined'){var lang={}};
lang.system_config_873='Page speed was boosted using Rapid Retrieval';
lang.system_config_874='The current REDCap webpage was able to load faster because it utilized REDCap\'s Rapid Retrieval feature. Rapid Retrieval is an automated internal feature that allows REDCap to store      certain pages in a temporary holding cache. When utilizing Rapid Retrieval, if no data or metadata has changed in the project recently, REDCap will output the stored cache of the page from when it was previously loaded.      This means that REDCap does not have to do all the work of normally loading the page but instead can load the page much faster by using the cache. The time that the current page was last cached was';
lang.docs_1136='ERROR: The file cannot be uploaded because its file type is not permitted.';
lang.alerts_24='Alert';
lang.calendar_popup_01='Close';
lang.calendar_widget_choosedatehint='Click to select a date';
lang.calendar_widget_choosetime='Choose Time';
lang.calendar_widget_done='Done';
lang.calendar_widget_hour='Hour';
lang.calendar_widget_min='Minute';
lang.calendar_widget_sec='Second';
lang.calendar_widget_month_jan='Jan';
lang.calendar_widget_month_feb='Feb';
lang.calendar_widget_month_mar='Mar';
lang.calendar_widget_month_apr='Apr';
lang.calendar_widget_month_may='May';
lang.calendar_widget_month_jun='Jun';
lang.calendar_widget_month_jul='Jul';
lang.calendar_widget_month_aug='Aug';
lang.calendar_widget_month_sep='Sep';
lang.calendar_widget_month_oct='Oct';
lang.calendar_widget_month_nov='Nov';
lang.calendar_widget_month_dec='Dec';
lang.calendar_widget_month_day_long_sun='Sunday';
lang.calendar_widget_month_day_long_mon='Monday';
lang.calendar_widget_month_day_long_tues='Tuesday';
lang.calendar_widget_month_day_long_wed='Wednesday';
lang.calendar_widget_month_day_long_thurs='Thursday';
lang.calendar_widget_month_day_long_fri='Friday';
lang.calendar_widget_month_day_long_sat='Saturday';
lang.calendar_widget_month_day_short_sun='Su';
lang.calendar_widget_month_day_short_mon='Mo';
lang.calendar_widget_month_day_short_tues='Tu';
lang.calendar_widget_month_day_short_wed='We';
lang.calendar_widget_month_day_short_thurs='Th';
lang.calendar_widget_month_day_short_fri='Fr';
lang.calendar_widget_month_day_short_sat='Sa';
lang.calendar_widget_next='Next';
lang.calendar_widget_prev='Prev';
lang.dash_72='Enable color-blind accessibility';
lang.dash_73='Disable color-blind accessibility';
lang.dashboard_32='Today';
lang.design_401='Okay';
lang.design_718='Valid';
lang.design_839='Special Functions';
lang.edit_project_186='Learn how to use';
lang.form_renderer_29='Now';
lang.global_13='Time';
lang.global_53='Cancel';
lang.global_146='Smart Variables';
lang.global_147='REDCap Auto Logout Warning';
lang.global_148='Log In';
lang.global_149='Continue on this page';
lang.global_150='You will be automatically logged out of REDCap in <b>2 MINUTES due to inactivity. Click the button below to prevent auto logout.';
lang.global_151='You will be automatically logged out of REDCap in <b>30 SECONDS due to inactivity. Click the button below to prevent auto logout.';
lang.global_152='<b>Due to inactivity, your REDCap session has expired. Click the button below to log in again.';
lang.global_167='Regular View Mode';
lang.global_168='Fullscreen Mode';
lang.global_169='Update & Close Editor';
lang.global_170='Logic Editor';
lang.global_171='Error in syntax';
lang.global_172='(The determination of validity may not be 100% accurate in all contexts.)';
lang.global_173='Enter new logic here';
lang.design_482='Codebook';
lang.design_962='or open the';
lang.global_132='Action Tags';
lang.global_208='Use the text box below to compose your logic, calculation, action tags, etc. If you need more space, click the Fullscreen Mode button to enlarge the text box. When you are finished, click the \'Update\' button to minimize the Editor window.';
lang.messaging_118='(click to go to project)';
lang.messaging_119='(current project)';
lang.messaging_177='NOTICE: It appears that you may have multiple browser windows/tabs open, which may prevent some things from working on this page until this page is refreshed. It is advised that you complete what you are doing, and then refresh this page.';
lang.docs_83='Drag and drop files here to upload';
lang.global_272='Upload a file';
lang.docs_81='Upload Error!';
lang.sendit_03='File could not be loaded because it is too large';
lang.sendit_04='Files must be smaller than';
lang.sendit_05='for uploading.';
lang.period='.';
lang.global_266='TIP: Your logic and calculations may contain <b>comments, which are not evaluated but only serve as annotations to help document or explain what the calc/logic is doing.  Comments must be on their own lines and start with // (double forward slash) or # (hash sign),  optionally preceded by whitespace characters (spaces, tabs). You may not append a comment to a line that is part of the logic or calc expression.';
lang.global_267='View example';
lang.global_272='Upload a file';
lang.global_273='Drop a file or click here<br>to upload an attachment';
lang.global_274='NOTE: Any files uploaded here using the rich text editor will be given a <b>publicly accessible download link that will be placed into the text,  in which anyone in possession of that link (including people not logged into REDCap) will be able to download the file at any time.  Files containing <b>confidential or sensitive information (e.g., PHI or PII) should *not* be uploaded here.  Additionally, all files uploaded here can be later accessed and/or deleted in the File Repository\'s "Miscellaneous File Attachments" folder,  whose contents does not count against the total amount of file storage used in the project. ';
lang.global_275='Auto-fill form';
lang.control_center_4803='Database Query Tool';
lang.docs_81='Upload Error!';
lang.docs_82='File did not upload:';
lang.data_entry_63='Max file size:';
lang.design_08='Working &hellip;';

	The code block below illustrates how one might use # and // as comments in your logic and calculations.
	# Text can be put here to explain what the logic/calculation does and why.
if ([field1] = '1' and [field2] > 7,

	// This comment can explain what the next line does.
	[score] * [factor],

	// Return '0' if the condition is False.
	0
)

	
	// Admin privileges
	var super_user = 0;
	var super_user_not_impersonator = 0;
	var admin_rights = '0';
	var account_manager = '0';
	var access_system_config = '0';
	var access_system_upgrade = '0';
	var access_external_module_install = '0';
	var access_admin_dashboards = '0';
		// System values
	var redcap_version = '15.0.20';
	var server_name = 'localhost';
	var app_path_webroot = '/redcap_v15.0.20/';
    var app_path_webroot_parent = '/';
	var app_path_webroot_full = 'http://localhost/';
	var app_path_survey_full = 'http://localhost/surveys/';
	var app_path_images = '/redcap_v15.0.20/Resources/images/';
	var page = 'Plugins/index.php';
    var secondary_pk = '';
	var sendit_enabled = 1;
	var surveys_enabled = 0;
	var mycap_enabled = 0;
	var reports_allow_public = '1';
	var rich_text_image_embed_enabled = 1;
	var rich_text_attachment_embed_enabled = 1;
	var now = '2025-05-01 01:42:29'; var now_mdy = '05-01-2025 01:42:30'; var now_dmy = '01-05-2025 01:42:30';
	var today = '2025-05-01'; var today_mdy = '05-01-2025'; var today_dmy = '01-05-2025';
	var email_domain_allowlist = new Array();
	var user_date_format_jquery = 'mm/dd/yy';
	var user_date_format_validation = 'mdy';
	var user_date_format_delimiter = '/';
	var csv_delimiter = ',';
	var ALLOWED_TAGS = '<blockquote><address><progress><meter><abbr><input><button><col><colgroup><strike><s><style><code><video><audio><source><caption><canvas><ol><ul><li><label><pre><p><a><br><center><font><b><i><u><h6><h5><h4><h3><h2><h1><hr><table><tbody><tr><th><td><thead><tfoot><img><span><div><em><strong><acronym><sub><sup><map><area>';
	var AUTOMATE_ALL = '0';
    var restricted_upload_file_types = ["ade","adp","apk","appx","appxbundle","bat","cab","chm","cmd","com","cpl","diagcab","diagcfg","diagpack","dll","dmg","ex","exe","hta","img","ins","iso","isp","jar","jnlp","js","jse","lib","lnk","mde","msc","msi","msix","msixbundle","msp","mst","nsh","php","pif","ps1","scr","sct","shb","sys","vb","vbe","vbs","vhd","vxd","wsc","wsf","wsh","xll"];
	var cookie_samesite = '';
	var cookie_secure = false;
		var datatables_disable = [];
	var fakeObjectTag = 'objectnznsogdsandmznrrbgdmzfhur1fptzhxvwvqatlpnfiwa0u9';
    var maxUploadSizeAttachment = 134217728; // bytes
    var canConvertPdfToImages = 1;
    var openAIImproveTextServiceEnabled = 0;
	function setDatePickerDefaults() {
		$.datepicker.setDefaults({
			timeText: window.lang.global_13,
			hourText: window.lang.calendar_widget_hour,
			minuteText: window.lang.calendar_widget_min,
			closeText: window.lang.calendar_widget_done,
			prevText: window.lang.calendar_widget_prev,
			nextText: window.lang.calendar_widget_next,
			currentText: window.lang.dashboard_32,
			monthNamesShort:[
				window.lang.calendar_widget_month_jan,
				window.lang.calendar_widget_month_feb,
				window.lang.calendar_widget_month_mar,
				window.lang.calendar_widget_month_apr,
				window.lang.calendar_widget_month_may,
				window.lang.calendar_widget_month_jun,
				window.lang.calendar_widget_month_jul,
				window.lang.calendar_widget_month_aug,
				window.lang.calendar_widget_month_sep,
				window.lang.calendar_widget_month_oct,
				window.lang.calendar_widget_month_nov,
				window.lang.calendar_widget_month_dec,
			],
			dayNames:[
				window.lang.calendar_widget_month_day_long_sun,
				window.lang.calendar_widget_month_day_long_mon,
				window.lang.calendar_widget_month_day_long_tues,
				window.lang.calendar_widget_month_day_long_wed,
				window.lang.calendar_widget_month_day_long_thurs,
				window.lang.calendar_widget_month_day_long_fri,
				window.lang.calendar_widget_month_day_long_sat,
			],
			dayNamesMin:[
				window.lang.calendar_widget_month_day_short_sun,
				window.lang.calendar_widget_month_day_short_mon,
				window.lang.calendar_widget_month_day_short_tues,
				window.lang.calendar_widget_month_day_short_wed,
				window.lang.calendar_widget_month_day_short_thurs,
				window.lang.calendar_widget_month_day_short_fri,
				window.lang.calendar_widget_month_day_short_sat,
			],
			isRTL: REDCap.MultiLanguage && typeof REDCap.MultiLanguage.isRTL == 'function' ? REDCap.MultiLanguage.isRTL() : false
		});
	}
	$(function(){
		setDatePickerDefaults();
	});
	
		$(function(){
			initAutoLogout(3,1440);
		});
		Working …

	
	0% means
	50% means
	100% means

	
	
		This value you provided is not a number. Please try again.
		This value you provided is not an integer. Please try again.
		The value entered is not a valid Vanderbilt Medical Record Number (i.e. 4- to 9-digit number, excluding leading zeros). Please try again.
		The value you provided must be within the suggested range
		The value you provided is outside the suggested range
		This value is admissible, but you may wish to double check it.
		The value entered must be a time value in the following format HH:MM within the range 00:00-23:59 (e.g., 04:32 or 23:19).
		This field must be a 5 or 9 digit U.S. ZIP Code (like 94043). Please re-enter it now.
		This field must be a 10 digit North American phone number (like 415 555 1212). Please re-enter it now.
		This field must be a valid email address (like joe@user.com). Please re-enter it now.
		The value you provided could not be validated because it does not follow the expected format. Please try again.
		Required format:
	
	
	
		if (typeof window.REDCap == 'undefined') {
			window.REDCap = {};
		}
		window.REDCap.validations = {};
				window.REDCap.validations['postalcode_french'] = {"datatype":"postal_code","regex":"\/^((0?[1-9])|([1-8][0-9])|(9[0-8]))[0-9]{3}$\/"};
				window.REDCap.validations['date_dmy'] = {"datatype":"date","regex":"\/^((29([-\\\/])02\\3(\\d{2}([13579][26]|[2468][048]|04|08)|(1600|2[048]00)))|((((0[1-9]|1\\d|2[0-8])([-\\\/])(0[1-9]|1[012]))|((29|30)([-\\\/])(0[13-9]|1[012]))|(31([-\\\/])(0[13578]|1[02])))(\\11|\\15|\\18)\\d{4}))$\/"};
				window.REDCap.validations['date_mdy'] = {"datatype":"date","regex":"\/^((02([-\\\/])29\\3(\\d{2}([13579][26]|[2468][048]|04|08)|(1600|2[048]00)))|((((0[1-9]|1[012])([-\\\/])(0[1-9]|1\\d|2[0-8]))|((0[13-9]|1[012])([-\\\/])(29|30))|((0[13578]|1[02])([-\\\/])31))(\\11|\\15|\\19)\\d{4}))$\/"};
				window.REDCap.validations['date_ymd'] = {"datatype":"date","regex":"\/^(((\\d{2}([13579][26]|[2468][048]|04|08)|(1600|2[048]00))([-\\\/])02(\\6)29)|(\\d{4}([-\\\/])((0[1-9]|1[012])(\\9)(0[1-9]|1\\d|2[0-8])|((0[13-9]|1[012])(\\9)(29|30))|((0[13578]|1[02])(\\9)31))))$\/"};
				window.REDCap.validations['datetime_dmy'] = {"datatype":"datetime","regex":"\/^((29([-\\\/])02\\3(\\d{2}([13579][26]|[2468][048]|04|08)|(1600|2[048]00)))|((((0[1-9]|1\\d|2[0-8])([-\\\/])(0[1-9]|1[012]))|((29|30)([-\\\/])(0[13-9]|1[012]))|(31([-\\\/])(0[13578]|1[02])))(\\11|\\15|\\18)\\d{4})) (\\d|[0-1]\\d|[2][0-3]):[0-5]\\d$\/"};
				window.REDCap.validations['datetime_mdy'] = {"datatype":"datetime","regex":"\/^((02([-\\\/])29\\3(\\d{2}([13579][26]|[2468][048]|04|08)|(1600|2[048]00)))|((((0[1-9]|1[012])([-\\\/])(0[1-9]|1\\d|2[0-8]))|((0[13-9]|1[012])([-\\\/])(29|30))|((0[13578]|1[02])([-\\\/])31))(\\11|\\15|\\19)\\d{4})) (\\d|[0-1]\\d|[2][0-3]):[0-5]\\d$\/"};
				window.REDCap.validations['datetime_ymd'] = {"datatype":"datetime","regex":"\/^(((\\d{2}([13579][26]|[2468][048]|04|08)|(1600|2[048]00))([-\\\/])02(\\6)29)|(\\d{4}([-\\\/])((0[1-9]|1[012])(\\9)(0[1-9]|1\\d|2[0-8])|((0[13-9]|1[012])(\\9)(29|30))|((0[13578]|1[02])(\\9)31)))) (\\d|[0-1]\\d|[2][0-3]):[0-5]\\d$\/"};
				window.REDCap.validations['datetime_seconds_dmy'] = {"datatype":"datetime_seconds","regex":"\/^((29([-\\\/])02\\3(\\d{2}([13579][26]|[2468][048]|04|08)|(1600|2[048]00)))|((((0[1-9]|1\\d|2[0-8])([-\\\/])(0[1-9]|1[012]))|((29|30)([-\\\/])(0[13-9]|1[012]))|(31([-\\\/])(0[13578]|1[02])))(\\11|\\15|\\18)\\d{4})) (\\d|[0-1]\\d|[2][0-3])(:[0-5]\\d){2}$\/"};
				window.REDCap.validations['datetime_seconds_mdy'] = {"datatype":"datetime_seconds","regex":"\/^((02([-\\\/])29\\3(\\d{2}([13579][26]|[2468][048]|04|08)|(1600|2[048]00)))|((((0[1-9]|1[012])([-\\\/])(0[1-9]|1\\d|2[0-8]))|((0[13-9]|1[012])([-\\\/])(29|30))|((0[13578]|1[02])([-\\\/])31))(\\11|\\15|\\19)\\d{4})) (\\d|[0-1]\\d|[2][0-3])(:[0-5]\\d){2}$\/"};
				window.REDCap.validations['datetime_seconds_ymd'] = {"datatype":"datetime_seconds","regex":"\/^(((\\d{2}([13579][26]|[2468][048]|04|08)|(1600|2[048]00))([-\\\/])02(\\6)29)|(\\d{4}([-\\\/])((0[1-9]|1[012])(\\9)(0[1-9]|1\\d|2[0-8])|((0[13-9]|1[012])(\\9)(29|30))|((0[13578]|1[02])(\\9)31)))) (\\d|[0-1]\\d|[2][0-3])(:[0-5]\\d){2}$\/"};
				window.REDCap.validations['email'] = {"datatype":"email","regex":"\/^(?!\\.)((?!.*\\.{2})[a-zA-Z0-9\\u0080-\\u02AF\\u0300-\\u07FF\\u0900-\\u18AF\\u1900-\\u1A1F\\u1B00-\\u1B7F\\u1D00-\\u1FFF\\u20D0-\\u214F\\u2C00-\\u2DDF\\u2F00-\\u2FDF\\u2FF0-\\u2FFF\\u3040-\\u319F\\u31C0-\\uA4CF\\uA700-\\uA71F\\uA800-\\uA82F\\uA840-\\uA87F\\uAC00-\\uD7AF\\uF900-\\uFAFF!#$%&'*+\\-\/=?^_`{|}~\\d]+)(\\.[a-zA-Z0-9\\u0080-\\u02AF\\u0300-\\u07FF\\u0900-\\u18AF\\u1900-\\u1A1F\\u1B00-\\u1B7F\\u1D00-\\u1FFF\\u20D0-\\u214F\\u2C00-\\u2DDF\\u2F00-\\u2FDF\\u2FF0-\\u2FFF\\u3040-\\u319F\\u31C0-\\uA4CF\\uA700-\\uA71F\\uA800-\\uA82F\\uA840-\\uA87F\\uAC00-\\uD7AF\\uF900-\\uFAFF!#$%&'*+\\-\/=?^_`{|}~\\d]+)*@(?!\\.)([a-zA-Z0-9\\u0080-\\u02AF\\u0300-\\u07FF\\u0900-\\u18AF\\u1900-\\u1A1F\\u1B00-\\u1B7F\\u1D00-\\u1FFF\\u20D0-\\u214F\\u2C00-\\u2DDF\\u2F00-\\u2FDF\\u2FF0-\\u2FFF\\u3040-\\u319F\\u31C0-\\uA4CF\\uA700-\\uA71F\\uA800-\\uA82F\\uA840-\\uA87F\\uAC00-\\uD7AF\\uF900-\\uFAFF\\-\\.\\d]+)((\\.([a-zA-Z\\u0080-\\u02AF\\u0300-\\u07FF\\u0900-\\u18AF\\u1900-\\u1A1F\\u1B00-\\u1B7F\\u1D00-\\u1FFF\\u20D0-\\u214F\\u2C00-\\u2DDF\\u2F00-\\u2FDF\\u2FF0-\\u2FFF\\u3040-\\u319F\\u31C0-\\uA4CF\\uA700-\\uA71F\\uA800-\\uA82F\\uA840-\\uA87F\\uAC00-\\uD7AF\\uF900-\\uFAFF]){2,63})+)$\/i"};
				window.REDCap.validations['integer'] = {"datatype":"integer","regex":"\/^[-+]?\\b\\d+\\b$\/"};
				window.REDCap.validations['integer1_20_999_997'] = {"datatype":"integer","regex":"\/^([1-9]|[1][0-9]|[2][0]|-[9][9][9]|-[9][9][7])$\/"};
				window.REDCap.validations['jhbvmrn_bv8d'] = {"datatype":"mrn","regex":"\/^([B])([V])\\d{8}$\/"};
				window.REDCap.validations['jheid_e9d'] = {"datatype":"mrn","regex":"\/^([E])\\d{9}$\/"};
				window.REDCap.validations['jhmrn_jh8d'] = {"datatype":"mrn","regex":"\/^([Jj])([Hh])\\d{8}$\/"};
				window.REDCap.validations['jhed_id'] = {"datatype":"text","regex":"\/^[a-z]+[0-9]+@jh.edu$\/"};
				window.REDCap.validations['jhed_id_short'] = {"datatype":"text","regex":"\/^[a-z]+[0-9]+$\/"};
				window.REDCap.validations['jhed_id_short_99999'] = {"datatype":"text","regex":"\/^[a-z]+[0-9]+$|99999\/"};
				window.REDCap.validations['jhed_id_email'] = {"datatype":"email","regex":"\/^[a-z]+[0-9]+@jh.edu$\/"};
				window.REDCap.validations['alpha_only'] = {"datatype":"text","regex":"\/^[a-z]+$\/i"};
				window.REDCap.validations['mrn_10d'] = {"datatype":"mrn","regex":"\/^\\d{10}$\/"};
				window.REDCap.validations['mrn_generic'] = {"datatype":"mrn","regex":"\/^[a-z0-9-_]+$\/i"};
				window.REDCap.validations['number'] = {"datatype":"number","regex":"\/^[-+]?[0-9]*\\.?[0-9]+([eE][-+]?[0-9]+)?$\/"};
				window.REDCap.validations['number_1dp_comma_decimal'] = {"datatype":"number_comma_decimal","regex":"\/^-?\\d+,\\d$\/"};
				window.REDCap.validations['number_1dp'] = {"datatype":"number","regex":"\/^-?\\d+\\.\\d$\/"};
				window.REDCap.validations['number_2dp_comma_decimal'] = {"datatype":"number_comma_decimal","regex":"\/^-?\\d+,\\d{2}$\/"};
				window.REDCap.validations['number_2dp'] = {"datatype":"number","regex":"\/^-?\\d+\\.\\d{2}$\/"};
				window.REDCap.validations['number_3dp_comma_decimal'] = {"datatype":"number_comma_decimal","regex":"\/^-?\\d+,\\d{3}$\/"};
				window.REDCap.validations['number_3dp'] = {"datatype":"number","regex":"\/^-?\\d+\\.\\d{3}$\/"};
				window.REDCap.validations['number_4dp_comma_decimal'] = {"datatype":"number_comma_decimal","regex":"\/^-?\\d+,\\d{4}$\/"};
				window.REDCap.validations['number_4dp'] = {"datatype":"number","regex":"\/^-?\\d+\\.\\d{4}$\/"};
				window.REDCap.validations['number_comma_decimal'] = {"datatype":"number_comma_decimal","regex":"\/^[-+]?[0-9]*,?[0-9]+([eE][-+]?[0-9]+)?$\/"};
				window.REDCap.validations['number_1dp_05'] = {"datatype":"number","regex":"\/^(\\d*|\\d*\\.[05])$\/"};
				window.REDCap.validations['date_partial_2'] = {"datatype":"text","regex":"\/^(1[0-2]|0[1-9])-(20\\d{2}|19\\d{2}|0(?!0)\\d|[1-9]\\d)$\/"};
				window.REDCap.validations['date_partial_1'] = {"datatype":"text","regex":"\/^(1[0-2]|0[1-9])\\\/(20\\d{2}|19\\d{2}|0(?!0)\\d|[1-9]\\d)$\/"};
				window.REDCap.validations['phone_australia'] = {"datatype":"phone","regex":"\/^(\\(0[2-8]\\)|0[2-8])\\s*\\d{4}\\s*\\d{4}$\/"};
				window.REDCap.validations['phone_france'] = {"datatype":"phone","regex":"\/^(?:(?:\\+|00)(?:33|262|508|590|594|596|687)[\\s.-]{0,3}(?:\\(0\\)[\\s.-]{0,3})?|0)[1-9](?:(?:[\\s.-]?\\d{2}){4}|\\d{2}(?:[\\s.-]?\\d{3}){2})$\/"};
				window.REDCap.validations['phone'] = {"datatype":"phone","regex":"\/^(?:\\(?([2-9]0[1-9]|[2-9]1[02-9]|[2-9][2-9][0-9]|800|811)\\)?)\\s*(?:[.-]\\s*)?([0-9]{3})\\s*(?:[.-]\\s*)?([0-9]{4})(?:\\s*(?:#|x\\.?|ext\\.?|extension)\\s*(\\d+))?$\/"};
				window.REDCap.validations['phone800'] = {"datatype":"phone","regex":"\/^(?:\\(?([2-9]0[1-9]|[2-9]1[02-9]|[2-9][2-9][0-9]|800)\\)?)\\s*(?:[.-]\\s*)?([2-9]1[02-9]|[2-9][02-9]1|[2-9][02-9]{2})\\s*(?:[.-]\\s*)?([0-9]{4})(?:\\s*(?:#|x\\.?|ext\\.?|extension)\\s*(\\d+))?$\/"};
				window.REDCap.validations['phone_uk'] = {"datatype":"phone","regex":"\/^((((\\+44|0044)\\s?\\d{4}|\\(?0\\d{4}\\)?)\\s?\\d{3}\\s?\\d{3})|(((\\+44|0044)\\s?\\d{3}|\\(?0\\d{3}\\)?)\\s?\\d{3}\\s?\\d{4})|(((\\+44|0044)\\s?\\d{2}|\\(?0\\d{2}\\)?)\\s?\\d{4}\\s?\\d{4}))(\\s?\\#(\\d{4}|\\d{3}))?$\/"};
				window.REDCap.validations['postalcode_australia'] = {"datatype":"postal_code","regex":"\/^\\d{4}$\/"};
				window.REDCap.validations['postalcode_canada'] = {"datatype":"postal_code","regex":"\/^[ABCEGHJKLMNPRSTVXY]{1}\\d{1}[A-Z]{1}\\s*\\d{1}[A-Z]{1}\\d{1}$\/i"};
				window.REDCap.validations['postalcode_germany'] = {"datatype":"postal_code","regex":"\/^(0[1-9]|[1-9]\\d)\\d{3}$\/"};
				window.REDCap.validations['postalcode_uk'] = {"datatype":"postal_code","regex":"\/^(([A-Z]{1,2}\\d{1,2})|([A-Z]{1,2}\\d[A-Z])) \\d[ABD-HJLNP-Z]{2}$\/"};
				window.REDCap.validations['ssn'] = {"datatype":"ssn","regex":"\/^\\d{3}-\\d\\d-\\d{4}$\/"};
				window.REDCap.validations['time_hh_mm_ss'] = {"datatype":"time","regex":"\/^(\\d|[01]\\d|(2[0-3]))(:[0-5]\\d){2}$\/"};
				window.REDCap.validations['time'] = {"datatype":"time","regex":"\/^([0-9]|[0-1][0-9]|[2][0-3]):([0-5][0-9])$\/"};
				window.REDCap.validations['time_mm_ss'] = {"datatype":"time","regex":"\/^[0-5]\\d:[0-5]\\d$\/"};
				window.REDCap.validations['vmrn'] = {"datatype":"mrn","regex":"\/^[0-9]{4,9}$\/"};
				window.REDCap.validations['zipcode'] = {"datatype":"postal_code","regex":"\/^\\d{5}(-\\d{4})?$\/"};
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			
		
	uizac4gnuWSgaMaBXfIszBdGQgkwhxZX
#container{ background: url("/redcap_v15.0.20/Resources/images/redcap-logo-large.png") no-repeat; }Log In
					This is the localhost machine. Feel free to play.
Please log in with your user name and password. If you are having trouble logging in, try clicking the "Forgot your password" link below.

				
					Username:
					
			
				
					Password:
					
			
			
				Log In
				Forgot your password?

			
			
	
    #pagecontainer { max-width: 1100px; }

			
            Go to My Projects
        
        
		
			REDCap is a secure web platform for building and managing online databases and surveys. REDCap's streamlined process for rapidly creating and designing projects offers a vast array of tools that can be tailored to virtually any data collection strategy.
		
		
			REDCap provides automated export procedures for seamless data downloads to Excel and common statistical packages (SPSS, SAS, Stata, R), as well as a built-in project calendar, a scheduling module, ad hoc reporting tools, and advanced features, such as branching logic, file uploading, and calculated fields.
		
		
			Learn more about REDCap by watching a
			 brief summary video (4 min).
			If you would like to view other quick video tutorials of REDCap in action and an overview of its features, please see the
			Training Resources
			page.
				Please note that any publication that results from a project utilizing REDCap should cite grant support
				(LOCALHOST).
			
	NOTICE: If you are collecting data for the purposes of human subjects research, review and approval of the project is required by your Institutional Review Board.


			If you require assistance or have any questions about REDCap, please contact
			LOCAL INSTANCE.
		LOCAL INSTANCE FOR TESTING ONLY
				
					Build online surveys and databases quickly and securely in your browser - Create and design your project using a secure login from any device. No extra software required. Access from anywhere, at any time.
				
				
					Fast and flexible - Go from project creation to starting data collection in less than one day. Customizations and changes are possible any time, even after data collection has begun.
								
					Advanced instrument design features - Auto-validation, calculated fields, file uploading, branching/skip logic, and survey stop actions.
							
                Diverse and flexible survey distribution options - Use a list of email addresses or phone numbers for your survey respondents and automatically contact them with personalized messages, and track who has responded. Or create a simple link for an anonymous survey for mass email mailings, to post on a website, or print on a flyer.
            		
                Data quality - Use field validation, branching/skip logic, and Missing Data Codes to improve and protect data quality during data entry. Open data queries to automatically identify and resolve discrepancies and other issues real-time. 
            
            
                Custom reporting - Create custom searches for generating reports to view aggregate data. Identify trends with built-in basic statistics and charts.
            
					Export data to common analysis packages - Export your data as a PDF or as CSV data for easy analysis in SAS, Stata, R, SPSS, or Microsoft Excel.
						
					Secure file storage and sharing - Upload and share any type of file with anyone in the world through the File Repository feature or Send-It tool. Also works with exports and other built-in file uploading features.
						
				Data-based triggers and alerts - Send real-time alerts and notifications to your team or other stakeholders via email, text, or phone based on certain data being entered or specific questions having a particular answer.
			
            Connect to other resources - Use built-in features (API) to move data to/from your project. Build your own custom software development features to connect your project to other systems.
		
			
		document.getElementById('username').focus();REDCap 15.0.20-© 2025 Vanderbilt University-Cookie policy
REDCap 15.0.20 - © 2025 Vanderbilt University