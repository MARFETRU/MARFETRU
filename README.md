classdef app1 < matlab.apps.AppBase

    % Properties that correspond to app components
    properties (Access = public)
        UIFigure                       matlab.ui.Figure
        SumatoriaNmerosConvertidosEditField  matlab.ui.control.NumericEditField
        SumatoriaNmerosConvertidosEditFieldLabel  matlab.ui.control.Label
        T                              matlab.ui.control.NumericEditField
        ResultadoNmero3EditFieldLabel  matlab.ui.control.Label
        S                              matlab.ui.control.NumericEditField
        ResultadoNmero2EditFieldLabel  matlab.ui.control.Label
        R                              matlab.ui.control.NumericEditField
        ResultadoNmero1EditFieldLabel  matlab.ui.control.Label
        X                              matlab.ui.control.DropDown
        SeleccioneBaseDropDownLabel    matlab.ui.control.Label
        CONVERTIRButton                matlab.ui.control.StateButton
        C                              matlab.ui.control.NumericEditField
        IngreseNmero3EditFieldLabel    matlab.ui.control.Label
        B                              matlab.ui.control.NumericEditField
        IngreseNmero2EditFieldLabel    matlab.ui.control.Label
        A                              matlab.ui.control.NumericEditField
        IngreseNmero1EditFieldLabel    matlab.ui.control.Label
        CONVERTIDORDEBASELabel         matlab.ui.control.Label
    end

    % Callbacks that handle component events
    methods (Access = private)

        % Value changed function: CONVERTIRButton
        function CONVERTIRButtonValueChanged(app, event)
         % Obtener la base seleccionada
    base = app.X.Value;
    
    % Convertir los números A, B y C a la base seleccionada
    app.A = dec2base(app.A, base);
    app.B = dec2base(app.B, base);
    app.C = dec2base(app.C, base);
        end

        % Value changed function: X
        function XValueChanged(app, event)
% Obtener el valor seleccionado desde la GUI
valor_seleccionado = app.X.Value;

% Asignar el nombre de la base según el valor seleccionado
switch valor_seleccionado
    case 2
        nombre_base = 'binaria';
    case 3
        nombre_base = 'ternaria';
    case 4
        nombre_base = 'cuaternaria';
    case 5
        nombre_base = 'quinternaria';
    case 6
        nombre_base = 'sextanaria';
    case 7
        nombre_base = 'septenaria';
    case 8
        nombre_base = 'octal';
    case 9
        nombre_base = 'nonaria';
    case 10
        nombre_base = 'decimal';
    case 11
        nombre_base = 'undecimal';
    case 12
        nombre_base = 'duodecimal';
    case 13
        nombre_base = 'tridecimal';
    case 14
        nombre_base = 'tetradecimal';
    case 15
        nombre_base = 'pentadecimal';
    otherwise
     
end

% Mostrar el nombre de la base
disp(['Base ', num2str(valor_seleccionado), ' = ', nombre_base]);

        end

        % Value changed function: SumatoriaNmerosConvertidosEditField
        function SumatoriaNmerosConvertidosEditFieldValueChanged(app, event)
            value = app.SumatoriaNmerosConvertidosEditField.Value;
            suma_convertidos = str2double(A_base) + str2double(B_base) + str2double(C_base);
        end
    end

    % Component initialization
    methods (Access = private)

        % Create UIFigure and components
        function createComponents(app)

            % Create UIFigure and hide until all components are created
            app.UIFigure = uifigure('Visible', 'off');
            app.UIFigure.Position = [100 100 640 480];
            app.UIFigure.Name = 'MATLAB App';

            % Create CONVERTIDORDEBASELabel
            app.CONVERTIDORDEBASELabel = uilabel(app.UIFigure);
            app.CONVERTIDORDEBASELabel.HorizontalAlignment = 'center';
            app.CONVERTIDORDEBASELabel.FontSize = 24;
            app.CONVERTIDORDEBASELabel.FontWeight = 'bold';
            app.CONVERTIDORDEBASELabel.Position = [172 424 300 48];
            app.CONVERTIDORDEBASELabel.Text = 'CONVERTIDOR DE BASE';

            % Create IngreseNmero1EditFieldLabel
            app.IngreseNmero1EditFieldLabel = uilabel(app.UIFigure);
            app.IngreseNmero1EditFieldLabel.HorizontalAlignment = 'right';
            app.IngreseNmero1EditFieldLabel.FontWeight = 'bold';
            app.IngreseNmero1EditFieldLabel.Position = [45 379 106 22];
            app.IngreseNmero1EditFieldLabel.Text = 'Ingrese Número 1';

            % Create A
            app.A = uieditfield(app.UIFigure, 'numeric');
            app.A.FontWeight = 'bold';
            app.A.Position = [159 377 43 26];
            app.A.Value = 35;

            % Create IngreseNmero2EditFieldLabel
            app.IngreseNmero2EditFieldLabel = uilabel(app.UIFigure);
            app.IngreseNmero2EditFieldLabel.HorizontalAlignment = 'right';
            app.IngreseNmero2EditFieldLabel.FontWeight = 'bold';
            app.IngreseNmero2EditFieldLabel.Position = [243 379 106 22];
            app.IngreseNmero2EditFieldLabel.Text = 'Ingrese Número 2';

            % Create B
            app.B = uieditfield(app.UIFigure, 'numeric');
            app.B.FontWeight = 'bold';
            app.B.Position = [357 377 43 26];
            app.B.Value = 35;

            % Create IngreseNmero3EditFieldLabel
            app.IngreseNmero3EditFieldLabel = uilabel(app.UIFigure);
            app.IngreseNmero3EditFieldLabel.HorizontalAlignment = 'right';
            app.IngreseNmero3EditFieldLabel.FontWeight = 'bold';
            app.IngreseNmero3EditFieldLabel.Position = [439 379 106 22];
            app.IngreseNmero3EditFieldLabel.Text = 'Ingrese Número 3';

            % Create C
            app.C = uieditfield(app.UIFigure, 'numeric');
            app.C.FontWeight = 'bold';
            app.C.Position = [553 377 43 26];
            app.C.Value = 35;

            % Create CONVERTIRButton
            app.CONVERTIRButton = uibutton(app.UIFigure, 'state');
            app.CONVERTIRButton.ValueChangedFcn = createCallbackFcn(app, @CONVERTIRButtonValueChanged, true);
            app.CONVERTIRButton.Text = 'CONVERTIR';
            app.CONVERTIRButton.FontSize = 24;
            app.CONVERTIRButton.FontWeight = 'bold';
            app.CONVERTIRButton.Position = [244 240 156 38];

            % Create SeleccioneBaseDropDownLabel
            app.SeleccioneBaseDropDownLabel = uilabel(app.UIFigure);
            app.SeleccioneBaseDropDownLabel.HorizontalAlignment = 'right';
            app.SeleccioneBaseDropDownLabel.FontSize = 14;
            app.SeleccioneBaseDropDownLabel.FontWeight = 'bold';
            app.SeleccioneBaseDropDownLabel.Position = [182 314 116 22];
            app.SeleccioneBaseDropDownLabel.Text = 'Seleccione Base';

            % Create X
            app.X = uidropdown(app.UIFigure);
            app.X.Items = {'Base 2', 'Base 3', 'Base 4', 'Base 5', 'Base 6', 'Base 7', 'Base 8', 'Base 9', 'Base 10', 'Base 11', 'Base 12', 'Base 13', 'Base 14', 'Base 15'};
            app.X.ValueChangedFcn = createCallbackFcn(app, @XValueChanged, true);
            app.X.FontSize = 14;
            app.X.FontWeight = 'bold';
            app.X.Position = [313 314 100 22];
            app.X.Value = 'Base 5';

            % Create ResultadoNmero1EditFieldLabel
            app.ResultadoNmero1EditFieldLabel = uilabel(app.UIFigure);
            app.ResultadoNmero1EditFieldLabel.HorizontalAlignment = 'right';
            app.ResultadoNmero1EditFieldLabel.FontWeight = 'bold';
            app.ResultadoNmero1EditFieldLabel.Position = [64 191 122 22];
            app.ResultadoNmero1EditFieldLabel.Text = 'Resultado Número 1';

            % Create R
            app.R = uieditfield(app.UIFigure, 'numeric');
            app.R.FontWeight = 'bold';
            app.R.Position = [92 164 65 26];

            % Create ResultadoNmero2EditFieldLabel
            app.ResultadoNmero2EditFieldLabel = uilabel(app.UIFigure);
            app.ResultadoNmero2EditFieldLabel.HorizontalAlignment = 'right';
            app.ResultadoNmero2EditFieldLabel.FontWeight = 'bold';
            app.ResultadoNmero2EditFieldLabel.Position = [261 191 122 22];
            app.ResultadoNmero2EditFieldLabel.Text = 'Resultado Número 2';

            % Create S
            app.S = uieditfield(app.UIFigure, 'numeric');
            app.S.FontWeight = 'bold';
            app.S.Position = [289 164 65 26];

            % Create ResultadoNmero3EditFieldLabel
            app.ResultadoNmero3EditFieldLabel = uilabel(app.UIFigure);
            app.ResultadoNmero3EditFieldLabel.HorizontalAlignment = 'right';
            app.ResultadoNmero3EditFieldLabel.FontWeight = 'bold';
            app.ResultadoNmero3EditFieldLabel.Position = [459 191 122 22];
            app.ResultadoNmero3EditFieldLabel.Text = 'Resultado Número 3';

            % Create T
            app.T = uieditfield(app.UIFigure, 'numeric');
            app.T.FontWeight = 'bold';
            app.T.Position = [487 164 65 26];

            % Create SumatoriaNmerosConvertidosEditFieldLabel
            app.SumatoriaNmerosConvertidosEditFieldLabel = uilabel(app.UIFigure);
            app.SumatoriaNmerosConvertidosEditFieldLabel.HorizontalAlignment = 'right';
            app.SumatoriaNmerosConvertidosEditFieldLabel.FontWeight = 'bold';
            app.SumatoriaNmerosConvertidosEditFieldLabel.Position = [227 108 193 22];
            app.SumatoriaNmerosConvertidosEditFieldLabel.Text = 'Sumatoria Números Convertidos';

            % Create SumatoriaNmerosConvertidosEditField
            app.SumatoriaNmerosConvertidosEditField = uieditfield(app.UIFigure, 'numeric');
            app.SumatoriaNmerosConvertidosEditField.ValueChangedFcn = createCallbackFcn(app, @SumatoriaNmerosConvertidosEditFieldValueChanged, true);
            app.SumatoriaNmerosConvertidosEditField.FontWeight = 'bold';
            app.SumatoriaNmerosConvertidosEditField.Position = [290 81 65 26];

            % Show the figure after all components are created
            app.UIFigure.Visible = 'on';
        end
    end

    % App creation and deletion
    methods (Access = public)

        % Construct app
        function app = app1

            % Create UIFigure and components
            createComponents(app)

            % Register the app with App Designer
            registerApp(app, app.UIFigure)

            if nargout == 0
                clear app
            end
        end

        % Code that executes before app deletion
        function delete(app)

            % Delete UIFigure when app is deleted
            delete(app.UIFigure)
        end
    end
end
