<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Memorial Garden Application - Bay View Association</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Arial, sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #f5f5f5;
            padding: 20px;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 2px solid #2c5aa0;
        }
        
        .header h1 {
            color: #2c5aa0;
            margin-bottom: 10px;
            font-size: 2em;
        }
        
        .header h2 {
            color: #2c5aa0;
            margin-bottom: 5px;
            font-size: 1.5em;
        }
        
        .form-section {
            margin-bottom: 30px;
            padding: 20px;
            background-color: #f9f9f9;
            border-radius: 5px;
        }
        
        .form-section h2 {
            color: #2c5aa0;
            margin-bottom: 15px;
            font-size: 1.4em;
        }
        
        .form-group {
            margin-bottom: 15px;
        }
        
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
            color: #555;
        }
        
        input[type="text"],
        input[type="email"],
        input[type="tel"],
        input[type="date"],
        input[type="number"],
        select,
        textarea {
            width: 100%;
            padding: 10px 12px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 14px;
            transition: border-color 0.3s;
        }
        
        input:focus,
        textarea:focus,
        select:focus {
            outline: none;
            border-color: #2c5aa0;
            box-shadow: 0 0 0 2px rgba(44, 90, 160, 0.1);
        }
        
        textarea {
            min-height: 80px;
            resize: vertical;
        }
        
        .two-column {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }
        
        .radio-group {
            margin: 10px 0;
        }
        
        .radio-group input[type="radio"] {
            width: auto;
            margin-right: 8px;
        }
        
        .radio-group label {
            display: inline-block;
            margin-left: 0;
            margin-right: 20px;
            font-weight: normal;
            cursor: pointer;
        }
        
        .btn-primary {
            background-color: #2c5aa0;
            color: white;
            padding: 15px 40px;
            font-size: 16px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            max-width: 400px;
            margin: 0 auto;
            display: block;
            transition: background-color 0.3s;
        }
        
        .btn-primary:hover {
            background-color: #1e3d6f;
        }
        
        .btn-primary:disabled {
            background-color: #ccc;
            cursor: not-allowed;
        }
        
        .required {
            color: red;
        }
        
        .fee-info {
            background-color: #e8f0ff;
            padding: 15px;
            border-radius: 5px;
            margin: 15px 0;
        }
        
        .fee-info table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .fee-info td {
            padding: 8px;
            border-bottom: 1px solid #ddd;
        }
        
        .fee-info td:first-child {
            font-weight: 600;
        }
        
        .policy-note {
            background-color: #fff3cd;
            border: 1px solid #ffeaa7;
            padding: 15px;
            border-radius: 5px;
            margin: 15px 0;
        }
        
        .policy-note h3 {
            color: #856404;
            margin-bottom: 10px;
        }
        
        .historic-note {
            background-color: #f8f9fa;
            border: 1px solid #dee2e6;
            padding: 15px;
            border-radius: 5px;
            margin: 20px 0;
            text-align: center;
            font-style: italic;
        }
        
        .payment-section {
            background-color: #f0f8ff;
            padding: 15px;
            border-radius: 5px;
            margin: 15px 0;
        }
        
        #memberDetails {
            margin-top: 15px;
            padding: 15px;
            background-color: #f8f9fa;
            border-radius: 5px;
            border-left: 4px solid #2c5aa0;
            display: none;
        }
        
        .loading {
            display: none;
            text-align: center;
            padding: 20px;
        }
        
        .loading::after {
            content: "";
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid #f3f3f3;
            border-top: 3px solid #2c5aa0;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        @media (max-width: 600px) {
            .two-column {
                grid-template-columns: 1fr;
            }
            
            .container {
                padding: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>Bay View Association</h1>
            <h2>Memorial Garden Application</h2>
            <p>Placement of Cremains</p>
        </div>
        
        <form action="https://formspree.io/f/mnnzqjkb" method="POST" id="memorialGardenForm">
            <!-- Hidden fields for form processing -->
            <input type="hidden" name="_subject" value="New Memorial Garden Application - Bay View Association">
            <input type="hidden" name="_next" value="data:text/html,<html><body style='font-family: Arial, sans-serif; text-align: center; padding: 50px; background-color: #f5f5f5;'><div style='max-width: 600px; margin: 0 auto; background: white; padding: 40px; border-radius: 8px; box-shadow: 0 2px 10px rgba(0,0,0,0.1);'><h2 style='color: #2c5aa0; margin-bottom: 20px;'>Application Submitted Successfully!</h2><p style='margin-bottom: 20px; font-size: 16px;'>Thank you for submitting your Memorial Garden application.</p><p style='margin-bottom: 20px;'>Your application has been received and will be reviewed by the Bay View Association Board of Trustees.</p><p style='margin-bottom: 20px;'><strong>Next Steps:</strong></p><ul style='text-align: left; margin-bottom: 20px;'><li>You will receive a confirmation email shortly</li><li>The Board will review your application</li><li>You will be contacted within 2 business days</li><li>Payment processing will begin upon approval</li></ul><p style='color: #666; font-size: 14px;'>A National Historic Landmark - Founded in 1875<br>Bay View Association<br>1715 Encampment Avenue, Petoskey, MI 49770</p></div></body></html>">
            <input type="hidden" name="form_type" value="Memorial Garden Application">
            <input type="hidden" name="submission_date" id="submissionDate">
            
            <!-- Purpose Section -->
            <div class="form-section">
                <h2>Purpose of Application</h2>
                <div class="form-group">
                    <label>Application Purpose <span class="required">*</span></label>
                    <div class="radio-group">
                        <input type="radio" id="immediatePayment" name="application_purpose" value="Payment for immediate placement of ashes" required>
                        <label for="immediatePayment">Payment for immediate placement of ashes</label>
                    </div>
                    <div class="radio-group">
                        <input type="radio" id="prepayment" name="application_purpose" value="Prepayment for future placement of ashes" required>
                        <label for="prepayment">Prepayment for future placement of ashes</label>
                    </div>
                </div>
            </div>
            
            <!-- Payment Information -->
            <div class="form-section">
                <h2>Payment Information</h2>
                <div class="fee-info">
                    <table>
                        <tr>
                            <td>Placement Fee (Bay View Members and relatives):</td>
                            <td>$400.00</td>
                        </tr>
                        <tr>
                            <td>Placement Fee (Non-Bay View Members):</td>
                            <td>$1,500.00</td>
                        </tr>
                    </table>
                    <p style="margin-top: 10px;"><strong>Note:</strong> Please make checks payable to "Bay View Association," with memo of "Memorial Garden."</p>
                    <p><strong>Mail to:</strong> Bay View Association, P.O. Box 583, Petoskey, MI 49770</p>
                </div>
                
                <div class="payment-section">
                    <div class="form-group">
                        <label for="payment_amount">Amount Enclosed ($) <span class="required">*</span></label>
                        <input type="number" id="payment_amount" name="payment_amount" step="0.01" min="0" required>
                    </div>
                    <div class="form-group">
                        <label for="deceased_name">Name(s) of deceased <span class="required">*</span></label>
                        <input type="text" id="deceased_name" name="deceased_name" required>
                    </div>
                </div>
            </div>
            
            <!-- Personal History Information -->
            <div class="form-section">
                <h2>Personal History Information</h2>
                <p style="margin-bottom: 15px; font-style: italic;">The following information about the interred individual is requested for the Memorial Garden archival file.</p>
                
                <div class="two-column">
                    <div class="form-group">
                        <label for="first_name">First Name <span class="required">*</span></label>
                        <input type="text" id="first_name" name="first_name" required>
                    </div>
                    <div class="form-group">
                        <label for="last_name">Last Name <span class="required">*</span></label>
                        <input type="text" id="last_name" name="last_name" required>
                    </div>
                </div>
                
                <div class="two-column">
                    <div class="form-group">
                        <label for="middle_name">Middle Name</label>
                        <input type="text" id="middle_name" name="middle_name">
                    </div>
                    <div class="form-group">
                        <label for="maiden_name">Maiden Name (if appropriate)</label>
                        <input type="text" id="maiden_name" name="maiden_name">
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="home_address">Permanent Home Address</label>
                    <input type="text" id="home_address" name="home_address" placeholder="Street, City, State, Zip">
                </div>
                
                <div class="form-group">
                    <label for="bayview_address">Bay View Address</label>
                    <input type="text" id="bayview_address" name="bayview_address" placeholder="Street, City, State, Zip">
                </div>
                
                <div class="two-column">
                    <div class="form-group">
                        <label for="birth_date">Date of Birth</label>
                        <input type="date" id="birth_date" name="birth_date">
                    </div>
                    <div class="form-group">
                        <label for="birth_place">Place of Birth</label>
                        <input type="text" id="birth_place" name="birth_place">
                    </div>
                </div>
                
                <div class="two-column">
                    <div class="form-group">
                        <label for="death_date">Date of Death</label>
                        <input type="date" id="death_date" name="death_date">
                    </div>
                    <div class="form-group">
                        <label for="placement_date">Date of Placement in Memorial Garden</label>
                        <input type="date" id="placement_date" name="placement_date">
                    </div>
                </div>
                
                <div class="two-column">
                    <div class="form-group">
                        <label for="mother_name">Mother's Name</label>
                        <input type="text" id="mother_name" name="mother_name">
                    </div>
                    <div class="form-group">
                        <label for="father_name">Father's Name</label>
                        <input type="text" id="father_name" name="father_name">
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="bayview_history">Bay View History (family, committees, role in community, etc.)</label>
                    <textarea id="bayview_history" name="bayview_history" rows="4" placeholder="Please describe the deceased's connection to Bay View Association..."></textarea>
                </div>
            </div>
            
            <!-- Contact Information -->
            <div class="form-section">
                <h2>Contact Information</h2>
                <div class="form-group">
                    <label for="contact_name">Contact Person Name <span class="required">*</span></label>
                    <input type="text" id="contact_name" name="contact_name" required>
                </div>
                <div class="form-group">
                    <label for="contact_address">Address <span class="required">*</span></label>
                    <input type="text" id="contact_address" name="contact_address" required>
                </div>
                <div class="two-column">
                    <div class="form-group">
                        <label for="contact_phone">Phone <span class="required">*</span></label>
                        <input type="tel" id="contact_phone" name="contact_phone" required>
                    </div>
                    <div class="form-group">
                        <label for="contact_email">Email</label>
                        <input type="email" id="contact_email" name="contact_email">
                    </div>
                </div>
            </div>
            
            <!-- Bay View Membership -->
            <div class="form-section">
                <h2>Bay View Membership Information</h2>
                <div class="form-group">
                    <label>Are you or the deceased a Bay View member or relative of a member? <span class="required">*</span></label>
                    <div class="radio-group">
                        <input type="radio" id="member_yes" name="is_member" value="Yes" required>
                        <label for="member_yes">Yes</label>
                    </div>
                    <div class="radio-group">
                        <input type="radio" id="member_no" name="is_member" value="No" required>
                        <label for="member_no">No</label>
                    </div>
                </div>
                <div id="memberDetails">
                    <div class="form-group">
                        <label for="member_name">Bay View Member Name</label>
                        <input type="text" id="member_name" name="member_name">
                    </div>
                    <div class="form-group">
                        <label for="member_relationship">Relationship to member</label>
                        <input type="text" id="member_relationship" name="member_relationship">
                    </div>
                </div>
            </div>
            
            <!-- Policies -->
            <div class="form-section">
                <h2>Memorial Garden Policies</h2>
                <div class="policy-note">
                    <h3>Important Information</h3>
                    <ul style="margin-left: 20px;">
                        <li>Only cremated remains are accepted in the Memorial Garden</li>
                        <li>All placements subject to approval by Bay View Board of Trustees</li>
                        <li>Bay View Association maintains the Memorial Garden in perpetuity</li>
                        <li>Individual grave markers or memorials are not permitted</li>
                        <li>Full payment is required before placement</li>
                    </ul>
                </div>
                
                <div class="form-group">
                    <div class="radio-group">
                        <input type="checkbox" id="policy_agreement" name="policy_agreement" value="I agree to all Memorial Garden policies" required style="width: auto; margin-right: 10px;">
                        <label for="policy_agreement" style="display: inline; font-weight: normal;">I have read and agree to comply with all Memorial Garden policies. I understand that all placements are subject to approval by the Bay View Board of Trustees.</label>
                    </div>
                </div>
            </div>
            
            <!-- Historic Note -->
            <div class="historic-note">
                <p><strong>A National Historic Landmark - Founded in 1875</strong></p>
                <p>1715 Encampment Avenue, Petoskey, Michigan 49770</p>
                <p>Phone: 231.347.6225 | BayViewAssociation.org</p>
            </div>
            
            <!-- Submit Section -->
            <div style="text-align: center; margin-top: 30px;">
                <div class="loading" id="loading">
                    <p>Submitting your application...</p>
                </div>
                <button type="submit" class="btn-primary" id="submitButton">Submit Memorial Garden Application</button>
            </div>
        </form>
    </div>
    
    <script>
        // Set submission date
        document.getElementById('submissionDate').value = new Date().toISOString();
        
        // Show/hide member details based on membership selection
        document.querySelectorAll('input[name="is_member"]').forEach(radio => {
            radio.addEventListener('change', function() {
                const memberDetails = document.getElementById('memberDetails');
                memberDetails.style.display = this.value === 'Yes' ? 'block' : 'none';
            });
        });
        
        // Set minimum dates to today
        const today = new Date().toISOString().split('T')[0];
        document.getElementById('placement_date').min = today;
        
        // Auto-populate deceased name when first/last name changes
        function updateDeceasedName() {
            const firstName = document.getElementById('first_name').value;
            const lastName = document.getElementById('last_name').value;
            const middleName = document.getElementById('middle_name').value;
            
            if (firstName || lastName) {
                const fullName = [firstName, middleName, lastName]
                    .filter(name => name && name.trim())
                    .join(' ');
                document.getElementById('deceased_name').value = fullName;
            }
        }
        
        document.getElementById('first_name').addEventListener('input', updateDeceasedName);
        document.getElementById('last_name').addEventListener('input', updateDeceasedName);
        document.getElementById('middle_name').addEventListener('input', updateDeceasedName);
        
        // Form submission handling
        document.getElementById('memorialGardenForm').addEventListener('submit', function(e) {
            const submitButton = document.getElementById('submitButton');
            const loading = document.getElementById('loading');
            
            // Show loading state
            submitButton.disabled = true;
            submitButton.textContent = 'Submitting...';
            loading.style.display = 'block';
            
            // Form will submit normally to Formspree
            // Loading state will be visible until redirect happens
        });
        
        // Improve form validation feedback
        document.querySelectorAll('input[required], textarea[required]').forEach(field => {
            field.addEventListener('invalid', function() {
                this.style.borderColor = '#dc3545';
            });
            
            field.addEventListener('input', function() {
                if (this.checkValidity()) {
                    this.style.borderColor = '#28a745';
                } else {
                    this.style.borderColor = '#ddd';
                }
            });
        });
    </script>
</body>
</html>
