@model AdmissionCollege.Models.PayMent

@{
    ViewBag.Title = "Create";
    Layout = null;
}

<h2>Create</h2>

@using (Html.BeginForm())
{
    @Html.AntiForgeryToken()

    <div class="container">
        <form id="pdfForm">
            <div class="row">
                <div class="col">
                    <h3 class="title">Billing Address</h3>

                    <div class="inputBox">
                        <label for="FullName">Full Name:</label>
                        @Html.TextBoxFor(model => model.FullName, new { @class = "form-control", @id = "FullName", @placeholder = "Enter your full name", required = "required" })
                        @Html.ValidationMessageFor(model => model.FullName, "", new { @class = "text-danger" })
                    </div>

                    <div class="inputBox">
                        <label for="Email">Email:</label>
                        @Html.TextBoxFor(model => model.Email, new { @class = "form-control", @id = "Email", @placeholder = "Enter email address", required = "required" })
                        @Html.ValidationMessageFor(model => model.Email, "", new { @class = "text-danger" })
                    </div>

                    <div class="inputBox">
                        <label for="Address">Address:</label>
                        @Html.TextBoxFor(model => model.Address, new { @class = "form-control", @id = "Address", @placeholder = "Enter address", required = "required" })
                        @Html.ValidationMessageFor(model => model.Address, "", new { @class = "text-danger" })
                    </div>

                    <div class="inputBox">
                        <label for="City">City:</label>
                        @Html.TextBoxFor(model => model.City, new { @class = "form-control", @id = "City", @placeholder = "Enter city", required = "required" })
                        @Html.ValidationMessageFor(model => model.City, "", new { @class = "text-danger" })
                    </div>

                    <div class="flex">
                        <div class="inputBox">
                            <label for="State">State:</label>
                            @Html.TextBoxFor(model => model.State, new { @class = "form-control", @id = "State", @placeholder = "Enter state", required = "required" })
                            @Html.ValidationMessageFor(model => model.State, "", new { @class = "text-danger" })
                        </div>

                        <div class="inputBox">
                            <label for="ZipCode">Zip Code:</label>
                            @Html.TextBoxFor(model => model.ZipCode, new { @class = "form-control", @id = "ZipCode", @placeholder = "123 456", required = "required" })
                            @Html.ValidationMessageFor(model => model.ZipCode, "", new { @class = "text-danger" })
                        </div>
                    </div>
                </div>

                <div class="col">
                    <h3 class="title">Payment</h3>

                    <div class="inputBox">
                        <label for="Cardaccepted">Card Accepted:</label>
                        <img src="https://media.geeksforgeeks.org/wp-content/uploads/20240715140014/Online-Payment-Project.webp" alt="credit/debit card image">
                        @Html.TextBoxFor(model => model.Cardaccepted, new { @class = "form-control", @id = "Cardaccepted", hidden = "hidden" })
                    </div>

                    <div class="inputBox">
                        <label for="Nameoncard">Name On Card:</label>
                        @Html.TextBoxFor(model => model.Nameoncard, new { @class = "form-control", @id = "Nameoncard", @placeholder = "Enter card name", required = "required" })
                        @Html.ValidationMessageFor(model => model.Nameoncard, "", new { @class = "text-danger" })
                    </div>

                    <div class="inputBox">
                        <label for="CreditCardNumber">Credit Card Number:</label>
                        @Html.TextBoxFor(model => model.CreditCardNumber, new { @class = "form-control", @id = "cardNum", @placeholder = "1111-2222-3333-4444", maxlength = "19", required = "required" })
                        @Html.ValidationMessageFor(model => model.CreditCardNumber, "", new { @class = "text-danger" })
                    </div>

                    <div class="inputBox">
                        <label for="ExpMonth">Exp Month:</label>
                        @Html.DropDownListFor(model => model.ExpMonth, new SelectList(new[] { "January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December" }), "Choose month", new { @class = "form-control" })
                        @Html.ValidationMessageFor(model => model.ExpMonth, "", new { @class = "text-danger" })
                    </div>

                    <div class="flex">
                        <div class="inputBox">
                            <label for="ExpYear">Exp Year:</label>
                            @Html.DropDownListFor(model => model.ExpYear, new SelectList(new[] { "2023", "2024", "2025", "2026", "2027" }), "Choose Year", new { @class = "form-control" })
                            @Html.ValidationMessageFor(model => model.ExpYear, "", new { @class = "text-danger" })
                        </div>

                        <div class="inputBox">
                            <label for="CVV">CVV</label>
                            @Html.TextBoxFor(model => model.CVV, new { @class = "form-control", @id = "CVV", @placeholder = "123", required = "required" })
                            @Html.ValidationMessageFor(model => model.CVV, "", new { @class = "text-danger" })
                        </div>
                    </div>
                </div>
            </div>

            <input type="submit" value="Proceed to Checkout" class="submit_btn" />
        </form>
    </div>
}

@section Scripts {
    <script type="text/javascript" src="~/Scripts/jquery-3.6.0.min.js"></script>
    <script type="text/javascript" src="~/Scripts/html2pdf.bundle.min.js"></script>
    <script>
        // Card formatting logic
        let cardNumInput = document.querySelector('#cardNum');
        cardNumInput.addEventListener('keyup', () => {
            let cNumber = cardNumInput.value.replace(/\s/g, "");
            if (Number(cNumber)) {
                cNumber = cNumber.match(/.{1,4}/g).join(" ");
                cardNumInput.value = cNumber;
            }
        });
    </script>
}
