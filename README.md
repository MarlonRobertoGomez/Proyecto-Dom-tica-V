public void popup (ImageButton posicion) 
{ 
    // Crea un objeto LayoutInflater para inflar el layout del popup 
    LayoutInflater inflater = (LayoutInflater) 
getSystemService(LAYOUT_INFLATER_SERVICE); 
 
    // Infla el layout del popup 
    View popupView = inflater.inflate(R.layout.pop_up_focos, null); 
 
    int width = ViewGroup.LayoutParams.MATCH_PARENT; 
    int height = ViewGroup.LayoutParams.WRAP_CONTENT; 
    boolean focusable = true; 
 
    // Inicializa el PopupWindow con el layout inflado 
    popupWindow = new PopupWindow(popupView, width, height, focusable); 
 
    // Obtiene los elementos del layout del popup y las asigna a sus 
variables 
    barra = popupView.findViewById(R.id.barra); 
    foco_submenu = popupView.findViewById(R.id.foco_submenu); 
    boton_azul = popupView.findViewById(R.id.boton_azul); 
    boton_rojo = popupView.findViewById(R.id.boton_rojo); 
    boton_blanco = popupView.findViewById(R.id.boton_blancos); 
 
    //Establece el listener de cambio de progreso para la SeekBar 
    barra.setOnSeekBarChangeListener(new 
SeekBar.OnSeekBarChangeListener() 
    { 
        @Override 
        public void onProgressChanged(SeekBar seekBar, int progress, 
boolean fromUser) 
        { 
            //Actualiza la imagen del foco_submenu según el progreso de 
la SeekBar 
            if (seekBar == barra) 
            { 
                if (progress == 0) 
                { 
                    foco_submenu.setImageResource(R.drawable.off); 
                } 
                else 
                { 
                    foco_submenu.setImageResource(R.drawable.on); 
                } 
            } 
        } 
        @Override 
        public void onStartTrackingTouch(SeekBar seekBar) 
        { 
 
        } 
        @Override 
        public void onStopTrackingTouch(SeekBar seekBar) 
        { 
 
        } 
    }); 

//Detecta el click para el botón azul del popup 
    boton_azul.setOnClickListener(new View.OnClickListener() 
    { 
        @Override 
        public void onClick(View v) 
        { 
            // Cambiar la imagen de foco_submenu con foco_azul 
            foco_submenu.setImageResource(R.drawable.foco_azul); 
        } 
    }); 
 
    //Detecta el click para el botón rojo del popup 
    boton_rojo.setOnClickListener(new View.OnClickListener() 
    { 
        @Override 
        public void onClick(View v) 
        { 
            // Cambiar la imagen de foco_submenu con foco_rojo 
            foco_submenu.setImageResource(R.drawable.foco_rojo); 
        } 
    }); 
 
    //Detecta el click para el botón blanco del popup 
    boton_blanco.setOnClickListener(new View.OnClickListener() 
    { 
        @Override 
        public void onClick(View v) 
        { 
            // Cambiar la imagen de foco_submenu con foco_azul 
            foco_submenu.setImageResource(R.drawable.on); 
        } 
    }); 
 
    // Establece el listener de toque para el layout del popup 
    popupView.setOnTouchListener(new View.OnTouchListener() 
    { 
        @Override 
        public boolean onTouch(View v, MotionEvent event) 
        { 
            //Cierra la ventana emergente cuando se toca fuera de ella 
            popupWindow.dismiss(); 
            return true; 
        } 
    }); 
    //Muestra la ventana emergente en el centro de la pantalla 
    popupWindow.showAtLocation(posicion, Gravity.CENTER, 0, 0); 
 
} 
