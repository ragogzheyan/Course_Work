
| Column Name                | Description                                                              | Data Type |
|---------------------------:|--------------------------------------------------------------------------|:---------:|
| brand                     | Manufacturer / brand name of the vehicle                                 | **object** |
| car_model                 | Specific model name or trim                                              | **object** |
| top_speed_kmh             | Manufacturer-claimed top speed in kilometers per hour                    | **int64** |
| battery_capacity_kWh      | Usable battery capacity in kilowatt-hours                                | **float64** |
| battery_type              | Battery chemistry / type (e.g., Lithium-ion)                             | **object** |
| number_of_cells           | Total number of battery cells in the pack                                | **float64** |
| torque_nm                 | Peak torque in Newton-meters                                             | **float64** |
| efficiency_wh_per_km      | Energy consumption in watt-hours per kilometer                           | **int64** |
| range_km                  | WLTP / manufacturer range in kilometers                                  | **float64** |
| acceleration_0_100_s      | 0–100 km/h acceleration time in seconds                                  | **float64** |
| fast_charging_power_kw_dc | Maximum DC fast-charging power in kilowatts                              | **float64** |
| fast_charge_port          | Fast-charge port standard (e.g., CCS, CHAdeMO)                           | **object** |
| towing_capacity_kg        | Towing capacity in kilograms (0 if not specified or not supported)       | **float64** |
| cargo_volume_l            | Boot / cargo volume in liters                                            | **float64** |
| seats                     | Number of passenger seats                                                | **int64** |
| drivetrain                | Drive layout (FWD, RWD, AWD)                                             | **object** |
| segment                   | Market segment / size class (e.g., B - Compact, JC - Medium)             | **object** |
| length_mm                 | Overall vehicle length in millimeters                                    | **int64** |
| width_mm                  | Overall vehicle width in millimeters                                     | **int64** |
| height_mm                 | Overall vehicle height in millimeters                                    | **int64** |
| car_body_type             | Body style (Hatchback, SUV, Sedan, etc.)                                 | **object** |
| torque_nm_mapped	        | Mapped convert torque from Newton-meters to lb-feet                      | **float64** | 
| manufacturing_country     | Country of brand origin                                                  | **object** |
| power_to_weight_ratio     | Power-to-weight ratio (unitless; as provided in dataset)                 | **float64** |
| efficiency                | Derived efficiency metric (unitless or dataset-specific scale)           | **float64** |
| power_to_weight_category  | Power-to-weight category ('Low', 'Medium', 'High')                       | **category** |