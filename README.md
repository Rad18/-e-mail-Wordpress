# -e-mail-Wordpress
Отправка уведомлений на e-mail при обновлении профиля пользователя
будет уведомлять пользователей по-email в случае, если кто-то (либо они сами) обновил информацию в их профиле на сайте.
function notify_me_by_email( $id ) {
    $website = get_bloginfo('wpurl');
    $user = get_userdata( $id );
    $to = $user->user_email;
    $subject = "Обновление профиля на сайте: ".$website."";
    $message = "Привет, " . $user->display_name . "!nВаш профиль был обновлён!nnСпасибо за посещение нашего сайта.n".$website."";
    wp_mail( $to, $subject, $message);
}
add_action( 'profile_update', 'notify_me_by_email', 10, 2);
