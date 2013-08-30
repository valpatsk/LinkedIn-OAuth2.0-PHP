LinkedIn.OAuth2.class
=====================

Please take OAuth2.class.php from my repo OAuth2.0-class https://github.com/valpatsk/OAuth2.0-class .

LinkedIn OAuth 2.0 Class.
Most necessary functions to interact with LinkedIn through OAuth 2.0.

HOW TO USE:

1. Redirect user to Auth screen:
<pre>
require_once("LinkedIn.OAuth2.class.php");
//Create LinkedIn app to get keys
$linkedin_api_key = "...";
$linkedin_secret = "...";
//put here your redirect url
$redirect_url="...";
$LIOAuth = new LinkedInOAuth2();
$connect_link = $LIOAuth->getAuthorizeUrl($linkedin_api_key,$redirect_url);
//show link or just redirect
</pre>


2. Get Access Token
<pre>
require_once("LinkedIn.OAuth2.class.php");
$linkedin_api_key = "...";
$linkedin_secret = "...";
//put here your redirect url
$redirect_url="...";
$code = isset($_REQUEST['code'])?$_REQUEST['code']:'';
$LIOAuth = new LinkedInOAuth2();
//you can put code as argument or it will be taken from $_REQUEST
$access_token = $LIOAuth->getAccessToken($linkedin_api_key,$linkedin_secret,$redirect_url,$code);
//you can already use $LIOAuth object
$LIOAuth->getProfile();
//How to use futher with existing access_token:
$LIOAuth = new LinkedInOAuth2($access_token);
</pre>


3. List of possible methods
<pre>
getProfile();
getUserProfile($user_id);
getConnections();
getGroups();
getGroup($group_id);
getCompanies();
getCompany($company_id);
getAdminCompanies();
getFollowedCompanies();
getStatuses($self = false, $start=0,$count = 20);
getUserStatuses($user_id, $self = true, $start=0,$count = 20);
getGroupPosts($group_id, $start=0,$count = 20, $order="", $category="",$role="");
getCompanyUpdates($company_id, $start=0,$count = 20);
getGroupPostResponses($post_id, $start = 0);
getNetworkPostResponses($update_key);
getCompanyUpdateResponses($company_id,$update_id);
shareStatus($args=array()); // $args=array('comment'=>'...','title'=>'...','submitted-url'=>'...','submitted-image-url'=>'...','description'=>'...')
postToGroup($group_id,$title,$message,$content=array());// $content=array('title'=>'...','submitted-url'=>'...','submitted-image-url'=>'...','description'=>'...')
postToCompany($company_id,$message,$content=array()); // $content=array('title'=>'...','submitted-url'=>'...','submitted-image-url'=>'...','description'=>'...')
deleteFromGroup($post_id);
commentToGroupPost($post_id,$response_text);
commentToNetworkPost($post_id,$response_text);
</pre>
