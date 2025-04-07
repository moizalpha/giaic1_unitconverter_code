import streamlit as st

# Title of the app
st.title("Unit Converter")

# Dropdown for unit selection
conversion_type = st.selectbox("Select Conversion Type", ["Length", "Temperature", "Weight"])

if conversion_type == "Length":
    st.header("Length Converter")
    units = {"Meters": 1, "Kilometers": 0.001, "Centimeters": 100, "Millimeters": 1000}
    input_unit = st.selectbox("From", list(units.keys()))
    output_unit = st.selectbox("To", list(units.keys()))
    value = st.number_input("Enter value", min_value=0.0, step=0.1)
    if st.button("Convert"):
        result = value * (units[output_unit] / units[input_unit])
        st.write(f"{value} {input_unit} = {result} {output_unit}")

elif conversion_type == "Temperature":
    st.header("Temperature Converter")
    input_unit = st.selectbox("From", ["Celsius", "Fahrenheit", "Kelvin"])
    output_unit = st.selectbox("To", ["Celsius", "Fahrenheit", "Kelvin"])
    value = st.number_input("Enter value", step=0.1)
    if st.button("Convert"):
        if input_unit == "Celsius":
            if output_unit == "Fahrenheit":
                result = (value * 9/5) + 32
            elif output_unit == "Kelvin":
                result = value + 273.15
            else:
                result = value
        elif input_unit == "Fahrenheit":
            if output_unit == "Celsius":
                result = (value - 32) * 5/9
            elif output_unit == "Kelvin":
                result = (value - 32) * 5/9 + 273.15
            else:
                result = value
        elif input_unit == "Kelvin":
            if output_unit == "Celsius":
                result = value - 273.15
            elif output_unit == "Fahrenheit":
                result = (value - 273.15) * 9/5 + 32
            else:
                result = value
        st.write(f"{value} {input_unit} = {result} {output_unit}")

elif conversion_type == "Weight":
    st.header("Weight Converter")
    units = {"Kilograms": 1, "Grams": 1000, "Pounds": 2.20462, "Ounces": 35.274}
    input_unit = st.selectbox("From", list(units.keys()))
    output_unit = st.selectbox("To", list(units.keys()))
    value = st.number_input("Enter value", min_value=0.0, step=0.1)
    if st.button("Convert"):
        result = value * (units[output_unit] / units[input_unit])
        st.write(f"{value} {input_unit} = {result} {output_unit}")
