Route::get('/clientes/vip', function () {

    // Creamos la lista de clientes
    $clientes = [
        (object)[
            'id' => 1,
            'nombre' => 'Andrea Martínez',
            'telefono' => '+503 71234567',
            'puntos_acumulados' => 42
        ],
        (object)[
            'id' => 2,
            'nombre' => 'José Ramírez',
            'telefono' => '+503 73456789',
            'puntos_acumulados' => 18
        ],
        (object)[
            'id' => 3,
            'nombre' => 'María Fernández',
            'telefono' => '+503 75678901',
            'puntos_acumulados' => 35
        ]
    ];

    // Creamos la tabla con los registros del cliente de forma dinámica
    $html = '
        <h2>Clientes VIP</h2>

        <table border=1 cellspacing=0>
            <thead>
                <tr>
                    <th>ID CLIENTE</th>
                    <th>NOMBRE</th>
                    <th>TELÉFONO</th>
                    <th>PUNTOS ACUMULADOS</th>
                </tr>
            </thead>

            <tbody>
    ';

    foreach ($clientes as $cliente) {

        $html .= "
            <tr>
                <td>$cliente->id</td>
                <td>$cliente->nombre</td>
                <td>$cliente->telefono</td>
                <td>$cliente->puntos_acumulados</td>
            </tr>
        ";

    }

    $html .= '
            </tbody>
        </table>
    ';

    echo $html;

});


/* Ejercicio 2: Panel de Proveedores Internacionales */

Route::get('/proveedores/internacionales', function () {

    // Creamos la lista de proveedores
    $proveedores = [
        (object)[
            'empresa' => 'Laboratorios VidaPlus',
            'pais_origen' => 'Costa Rica',
            'Medicamento_Principal' => 'Ibuprofeno',
            'tiempo_entrega_dias' => 8
        ],
        (object)[
            'empresa' => 'Pharma Global',
            'pais_origen' => 'México',
            'Medicamento_Principal' => 'Omeprazol',
            'tiempo_entrega_dias' => 17
        ],
        (object)[
            'empresa' => 'Medicorp Internacional',
            'pais_origen' => 'Colombia',
            'Medicamento_Principal' => 'Azitromicina',
            'tiempo_entrega_dias' => 22
        ],
    ];

    // Creamos la tabla con los registros del proveedor de forma dinámica
    $html = '
        <h2>PROVEEDORES INTERNACIONALES</h2>

        <table border=1 cellspacing=0>
            <thead>
                <tr>
                    <th>EMPRESA</th>
                    <th>PAÍS ORIGEN</th>
                    <th>MEDICAMENTO PRINCIPAL</th>
                    <th>TIEMPO ENTREGA DÍAS</th>
                </tr>
            </thead>

            <tbody>
    ';

    foreach ($proveedores as $proveedor) {

        $tiempo = $proveedor->tiempo_entrega_dias;

        if ($proveedor->tiempo_entrega_dias > 15) {
            $tiempo .= " (Demora Crítica)";
        }

        $html .= "
            <tr>
                <td>$proveedor->empresa</td>
                <td>$proveedor->pais_origen</td>
                <td>$proveedor->Medicamento_Principal</td>
                <td>$tiempo</td>
            </tr>
        ";

    }

    $html .= '
            </tbody>
        </table>
    ';

    echo $html;

});


/* Ejercicio 3: Inventario Automatizado de Lotes de Medicamentos */

Route::get('/lotes/inventario', function () {

    // Creamos la lista de lotes
    $lotes = [
        (object)[
            'codigo_lote' => 'A101',
            'nombre_medicamento' => 'Metformina',
            'cantidad_cajas' => 20,
            'temperatura_requerida_celsius' => 4
        ],
        (object)[
            'codigo_lote' => 'B205',
            'nombre_medicamento' => 'Paracetamol',
            'cantidad_cajas' => 48,
            'temperatura_requerida_celsius' => 22
        ],
        (object)[
            'codigo_lote' => 'C309',
            'nombre_medicamento' => 'Salbutamol',
            'cantidad_cajas' => 12,
            'temperatura_requerida_celsius' => 5
        ],
    ];

    // Creamos la tabla con los registros del inventario de forma dinámica
    $html = '
        <h2>INVENTARIO AUTOMATIZADO DE LOTES DE MEDICAMENTOS</h2>

        <table border=1 cellspacing=0>
            <thead>
                <tr>
                    <th>CÓDIGO LOTE</th>
                    <th>NOMBRE MEDICAMENTO</th>
                    <th>CANTIDAD CAJAS</th>
                    <th>TEMPERATURA</th>
                </tr>
            </thead>

            <tbody>
    ';

    foreach ($lotes as $lote) {

        $medicamento = $lote->nombre_medicamento;

        if ($lote->temperatura_requerida_celsius <= 5) {
            $medicamento .= " [Requiere Cadena de Frío]";
        }

        $html .= "
            <tr>
                <td>$lote->codigo_lote</td>
                <td>$medicamento</td>
                <td>$lote->cantidad_cajas</td>
                <td>$lote->temperatura_requerida_celsius °C</td>
            </tr>
        ";

    }

    $html .= '
            </tbody>
        </table>
    ';

    echo $html;

});
