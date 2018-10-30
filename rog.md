
//▼テキストボックスをカスタムフィールドへ追加する

/* フォーム表示 */
function html_source_for_layout_custom_box() {
    $c_text = get_post_meta( $_GET['post'], 'c_text' );
    echo '<label for="c_text">テキスト</label> ';
    echo '<input type="text" name="c_text" value="'.$c_text[0].'">';
}

/* メタボックスに追加 */
function add_layout_custom_box() {
    add_meta_box('text_layout', 'テキスト入力', 'html_source_for_layout_custom_box', 'one_line_comment', 'normal', 'high');
}
  
/* カスタムフィールドの値をDBに保存 */
function save_custom_field_postdata( $post_id ) {
    $mydata = $_POST['c_text'];
    if ( "" == get_post_meta( $post_id, 'c_text' )) {
        add_post_meta( $post_id, 'c_text', $mydata, true ) ;
    } else if ( $mydata != get_post_meta( $post_id, 'c_text' )) {
        update_post_meta( $post_id, 'c_text', $mydata ) ;
    } else if ( "" == $mydata ) {
        delete_post_meta( $post_id, 'c_text' ) ;
    }
}

add_action('admin_menu', 'add_layout_custom_box');
add_action('save_post', 'save_custom_field_postdata');

//▲テキストボックスをカスタムフィールドへ追加する
