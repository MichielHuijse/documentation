# documentation
Personal documentation made public

// Form validation Drupal 8
  if ($form_id == 'the_form_id') {

    $field_title = $form['field_title']['widget'][0]['value']['#default_value'];
      // Loads the block object and gets the values of the field group.
    $storage = \Drupal::entityTypeManager()->getStorage('block_content');
    $query = $storage->getQuery()
      ->condition('field_title', $field_title);
    $hit = $query->execute();
    if (count($hit) > 1) {
      //
      $form['#validate'][] = 'my_custom_validate';
      function my_custom_validate(&$form, \Drupal\Core\Form\FormStateInterface $form_state){
        $form_state->setErrorByName('field_title', t('Kies een unieke naam. Deze beschrijving bestaat al.'));
      }
    }
  }
