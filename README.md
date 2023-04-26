function marketo_form_shortcode( $atts ) {
  $atts = shortcode_atts( array(
    'form_id' => '',
    'class' => '',
    'id' => ''
  ), $atts, 'marketo_form' );

  $form_id = $atts['form_id'];
  $class = $atts['class'];
  $id = $atts['id'];

  ob_start();
?>
  <form id="<?php echo $id; ?>" class="<?php echo $class; ?>" method="post">
    <script src="//app-AB12.marketo.com/js/forms2/js/forms2.min.js"></script>
    <form id="mktoForm_<?php echo $form_id; ?>"></form>
    <script type="text/javascript">
      MktoForms2.loadForm("//app-AB12.marketo.com", "123-XYZ-456", <?php echo $form_id; ?>);
    </script>
  </form>
<?php
  return ob_get_clean();
}
add_shortcode( 'marketo_form', 'marketo_form_shortcode' );
